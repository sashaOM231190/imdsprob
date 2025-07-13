# imdsprob

IMDSProb is a cross-platform probing and diagnostics tool for Azure Instance Metadata Service (IMDS). It allows you to simulate real-world access patterns, measure latency, log results, and optionally collect network traces. The tool supports both Azure SDK-based probing (respects proxy settings) and direct HTTP probing (bypasses proxy) across Windows, Linux, and container environments.


# Features
Probe the IMDS endpoint via:

- Azure SDK (ManagedIdentityCredential)

- Direct HTTP call with proxy bypass

- Collect statistics:

- Min, Max, Avg latency

- Total requests

- Slowest request and timestamp

## Supports:

- System-assigned and User-assigned Managed Identity

- Command-line parameterization

- Real-time cancellation via Ctrl+C

- Optional network tracing:

- Windows: Generates NetworkTrace.etl

- Linux: Generates NetworkTrace.pcapng

## Usage

IMDSProb.exe --req 10 --timeint 1000 --mode mic --identity sys --probtype Both --nettrace

| Parameter         | Description                                                                |        |                                                    |
| ----------------- | -------------------------------------------------------------------------- | ------ | -------------------------------------------------- |
| `--req <n>`       | Number of probe requests to send                                           |        |                                                    |
| `--timeint <n>`   | Time interval between probes (in milliseconds)                             |        |                                                    |
| `--mode mic`      | Use `ManagedIdentityCredential` for probing                                |        |                                                    |
| `--identity sys`  | Use system-assigned managed identity (`sys` or `user`)                     |        |                                                    |
| `--clientId <id>` | Client ID of user-assigned identity (required if `--identity user` is set) |        |                                                    |
| `--probtype <SDK,Direct,Both>`|Select probe type: Azure SDK, Direct HTTP, or both              |        |                                                    |
| `--nettrace`      | Enable network trace logging                                               |        |                                                    |
| `--logdir <path>` | Directory to store logs and network trace                                  |        |                                                    |


## Output

IMDSProbLog.txt — Log of probe results and errors.

Stats Summary — Printed on screen and written to log after completion or Ctrl+C.

NetworkTrace.etl / .pcapng — Network trace file depending on platform.


