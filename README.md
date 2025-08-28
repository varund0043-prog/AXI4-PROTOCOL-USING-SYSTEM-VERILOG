**Project Overview**
Implementation of AXI4 protocol using SystemVerilog

Features a complete AXI4 master-slave communication system

Includes advanced verification components: assertions, coverage, and scoreboard

Developed and tested on EDA Playground with Synopsys tools

** Architecture Components**
Package (axi_pkg.sv)
Defines global parameters:

ADDR_WIDTH = 32

DATA_WIDTH = 32

ID_WIDTH = 4

BURST_LEN = 4

MEM_DEPTH = 256

Interface (axi_if.sv)
Defines AXI4 protocol signals:

Write Address Channel (AW)

Write Data Channel (W)

Write Response Channel (B)

Read Address Channel (AR)

Read Data Channel (R)

Includes modports for master and slave connections

Master Module (axi_master.sv)
Implements AXI4 master functionality

Finite State Machine with states:

IDLE, SEND_AW, SEND_W, SEND_B, SEND_AR, RECEIVE_R

Generates sequential write data (incrementing pattern)

Includes protocol assertions for validation

Slave Module (axi_slave.sv)
Implements AXI4 slave with memory storage

Handles write and read operations

Supports error injection for response testing

256-depth memory array for data storage

Verification Components
Scoreboard (scoreboard.sv)
Tracks written and read data using queues

Provides data comparison functionality

Generates pass/fail reports

Assertions (assert_axi.sv)
Validates protocol compliance:

WLAST timing correctness

Handshake protocol adherence

Address stability during transactions

Coverage (coverage.sv)
Functional coverage tracking:

FSM state coverage

ID values coverage

Burst length coverage

Response type coverage

Testbench (tb_top.sv)
Instantiates master, slave, and verification components

Connects scoreboard to monitor transactions

Includes waveform dumping for debugging

Runs comprehensive test sequence
**Implementation Features**
Protocol Compliance: Full AXI4 channel implementation

Data Integrity: Scoreboard verification of write-read consistency

Error Testing: Configurable error injection in slave responses

Functional Coverage: Comprehensive coverage collection

Assertion Checking: Runtime protocol validation

** Test Results**
Simulation Output
Successful write and read transactions captured

Data pattern: Sequential increment from abcd0000

All write-read comparisons passed

Scoreboard report: "All data matched. Test PASSED"

Coverage Achieved
FSM state transitions covered

Multiple burst lengths tested

Various response types generated

ID value coverage completed

**EDA Playground Flow**
1. Setup
Selected Synopsys VCS simulator

Configured SystemVerilog compilation

Set up file dependencies in correct order:
axi_pkg.sv, axi_if.sv ,axi_master.sv, axi_slave.sv, scoreboard.sv, assert_axi.sv ,coverage.sv ,tb_top.sv
4. Analysis
Reviewed scoreboard results

Verified assertion compliance

Analyzed coverage metrics

Examined waveform patterns

**Key Features Verified**
Write Transaction Completion

Address channel handshake

Data transfer with proper WLAST signaling

Response acknowledgment

Read Transaction Completion

Read address handshake

Data return with RLAST signaling

Response code validation

Protocol Compliance

All handshake protocols maintained

Signal stability during transactions

Proper response generation

Data Integrity

Write data correctly stored in slave memory

Read data matches written values

Sequential data pattern maintained

** Project Structure**

axi4_project/
 axi_pkg.sv              # Package with parameters
 axi_if.sv               # Interface definition
 axi_master.sv           # AXI4 master implementation
 axi_slave.sv            # AXI4 slave with memory
 scoreboard.sv           # Data verification component
 assert_axi.sv           # Protocol assertions
 coverage.sv             # Functional coverage
 tb_top.sv               # Top testbench

**Usage Instructions**
Compile all SystemVerilog files with appropriate toolchain

Simulate using the provided testbench

Monitor console output for transaction details

Review scoreboard report for test results

Analyze coverage metrics for verification completeness

**Status**
AXI4 protocol implementation complete

 All verification components functional

 Testbench successfully validated

 Coverage goals achieved

 Ready for integration into larger systems
