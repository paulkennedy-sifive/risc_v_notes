RISC-V Notes
============

Source: [The RISC-V Instruction Set Manual, Volume I: Unprivileged
ISA](https://github.com/riscv/riscv-isa-manual/releases/download/draft-20200727-8088ba4/riscv-spec.pdf)

Introduction
------------

### RISC-V Hardware Platform Terminology

-   hart: RISC-V-compatible hardware thread
-   Also defined: RISC-V hardware platform, core, accelerator

### RISC-V Software Execution Environments and Harts

-   EEI (execution environment interface) defines the initial state of a
    program, the number and type of harts including:
    -   the privilege modes supported by the harts
    -   the accessibility and attributes of memory and I/O regions
    -   the behavior of all legal instructions executed on each hart
    -   the handling of any interrupts or exceptions raised during
        execution including environment calls
-   Implementation of EEI can be pure HW, pure SW, or mix
    -   Examples provided

### RISC-V ISA Overview

-   RISC-V ISA: base integer ISA + optional extensions
-   There are currently four base ISAs
    -   Each characterized by width of the integer registers and the
        corresponding size of the address space and by the number of
        integer registers
    -   Two primary base integer variants: RV32I and RV64I
-   An extension is either standard, custom, or non-conforming
    -   Each RISC-V instruction-set encoding is divided into: standard,
        reserved, and custom

### Memory

-   A hart has a 2<sup>XLEN</sup> byte-addressible addr space
-   The EEI determines the mapping of resources into a hart's addr space
-   Different addr ranges may:
    -   be vacant
    -   contain main memory
    -   contain one or more I/O devices
-   Reads/writes to I/O may have visible side effects, but accesses to
    main memory cannot
-   With multiple harts, the addr spaces may be entirely the same or
    entirely different, or partly the same
-   Each RISC-V instr may perform combination of implicit (including
    instr fetch and addr translation) and explicit memory accesses
-   Normally, an exception occurs when an access is performed to a
    memory region that does not support it
-   Except when otherwise specified, implicit reads that do not raise an
    exception that have no side effects may occur arbitrarily early and
    speculatively, even before the machine could possibly prove that the
    read will be needed
-   To ensure that certain implicit reads are ordered only after writes
    to the same memory locations, software must execute specific fence
    or cache-control instructions defined for this purpose
-   Default memory consistency model for RISC-V: Weak Memory Ordering
    (RVWMO); an implementation may use Total Store Ordering

### Base Insturction-Length Encoding

-   The base RISC-V ISA has fixed-length 32-bit instructions which must
    be aligned to 32-bit boundaries

RV32I Base Integer Instruction Set, Version 2.1
-----------------------------------------------

"Zifencei" Instruction-Fetch Fence, Version 2.0
-----------------------------------------------

RV32E Base Integer Instruction Set, Version 1.9
-----------------------------------------------

RV64I Base Integer Instruction Set, Version 2.1
-----------------------------------------------

RV128I Base Integer Instruction Set, Version 1.7
------------------------------------------------

"M" Standard Extension for Integer Multiplication and Division, Version 2.0
---------------------------------------------------------------------------

"A" Standard Extension for Atomic Instructions, Version 2.1
-----------------------------------------------------------

"Zicsr", Control and Status Register (CSR) Instructions, Version 2.0
--------------------------------------------------------------------

Counters
--------

"F" Standard Extension for Single-Precision Floating-Point, Version 2.2
-----------------------------------------------------------------------

"D" Standard Extension for Double-Precision Floating-Point, Version 2.2
-----------------------------------------------------------------------

"Q" Standard Extension for Quad-Precision Floating-Point, Version 2.2
---------------------------------------------------------------------

RVWMO Memory Consistency Model, Version 2.0
-------------------------------------------

"L" Standard Extension for Decimal Floating-Point, Version 0.0
--------------------------------------------------------------

"C" Standard Extension for Compressed Instructions, Version 2.0
---------------------------------------------------------------

"B" Standard Extension for Bit Manipulation, Version 0.0
--------------------------------------------------------

"J" Standard Extension for Dynamically Translated Languages, Version 0.0
------------------------------------------------------------------------

"T" Standard Extension for Transactional Memory, Version 0.0
------------------------------------------------------------

"P" Standard Extension for Packed-SIMD Instructions, Version 0.2
----------------------------------------------------------------

"V" Standard Extension for Vector Operations, Version 0.7
---------------------------------------------------------

"Zam" Standard Extension for Misaligned Atomics, v0.1
-----------------------------------------------------

"Ztso" Standard Extension for Total Store Ordering, v0.1
--------------------------------------------------------

RV32/64G Instruction Set Listings
---------------------------------

RISC-V Assembly Programmer's Handbook
-------------------------------------

Extending RISC-V
----------------

ISA Extension Naming Conventions
--------------------------------
