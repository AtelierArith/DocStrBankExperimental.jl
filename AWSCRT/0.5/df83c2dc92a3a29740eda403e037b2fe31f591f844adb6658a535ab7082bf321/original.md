Environment variables:

  * `AWS_CRT_MEMORY_TRACING`: Set to `0`, `1`, or `2` to enable memory tracing. Default is off. See `aws_mem_trace_level`.
  * `AWS_CRT_MEMORY_TRACING_FRAMES_PER_STACK`: Set the number of frames per stack for memory tracing. Default is the AWS library's default.
  * `AWS_CRT_LOG_LEVEL`: Set to `0` through `6` to enable logging. Default is off. See [`aws_log_level`](https://juliaservices.github.io/LibAwsCommon.jl/dev/#LibAwsCommon.aws_log_level).
  * `AWS_CRT_LOG_PATH`: Set to the log file path. Must be set if `AWS_CRT_LOG_LEVEL` is set.

Note: all the symbols in this package that begin with underscores are private and are not part of this package's published interface. Please don't use them.
