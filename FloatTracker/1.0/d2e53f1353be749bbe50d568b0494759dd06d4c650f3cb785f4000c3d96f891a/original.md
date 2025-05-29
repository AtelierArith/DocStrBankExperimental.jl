Struct containing all configuration for the logger.

## Fields

  * `filename::String` Basename of the file to write logs to.

    Constructors automatically prefix the timestamp to the beginning of this basename so the logs are grouped together chronologically.
  * `buffersize::Int` Number of logs to buffer in memory before writing to file.

    Defaults to 1000. Decrease if you are crashing without getting the logs that you need.
  * `printToStdOut::Bool` Whether or not to write logs to STDOUT; defaults  to `false`.
  * `allErrors::Bool` Record all errors in the `*_error_log.txt` file.
  * `cstg::Bool` Write logs in CSTG format.
  * `cstgLineNum::Bool` Include the line number in CSTG output.
  * `cstgArgs::Bool` Include arguments to functions in CSTG output.
  * `maxLogs::Union{Int,Unbounded}` Maximum number of events to log; defaults to `Unbounded`.
  * `maxFrames::Union{Int,Unbounded}` Maximum number of stack frames to print in logging; defaults to `Unbounded`.
  * `exclusions::Array{Symbol}` Events to not log; defaults to `[:prop]`.
