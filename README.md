# JTAG DPI Module

This module emulates a JTAG port for a remote debug bridge. It can be used
together with the [JTAG bridge](https://github.com/ethz-iis/riscv_jtag_server),
to debug an RTL simulation. It has been adapted from the OpenRISC debug
interface for the [PULP project](http://pulp.ethz.ch).

The module has been developed and tested with Mentor Graphics ModelSim, but
should work with other SystemVerilog compatible simulators.

## ModelSim Build

To use the module inside of ModelSim, it has to be built using the following
commands first:

    vlog -sv -dpiheader dpiheader.h jtag_dpi.sv
    vlog -64 -ccflags "-I./" jtag_dpi.c

Note that ModelSim automatically creates the `dpiheader.h` file.

The `-64` switch is necessary if you are using ModelSim in 64 bit mode.

## Usage

Contrary to the Verilog legacy VPI interface, the DPI interface is used
automatically with the simulation, there is no need to explictly specify the
shared library or object file.
