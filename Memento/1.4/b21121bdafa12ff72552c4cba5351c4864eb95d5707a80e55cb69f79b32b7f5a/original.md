```
FileRoller <: IO
```

Is responsible for managing a rolling log file.

# Fields

  * `prefix::AbstractString`: filename prefix for the log.
  * `folder::AbstractString`: directory where the log should be written.
  * `filepath::AbstractString`: the full filepath for the log
  * `file::IO`: the current file IO handle
  * `byteswritten::Int64`: keeps track of how many bytes have been written to the current file.
  * `max_sz::Int`: the maximum number of bytes written to a file before rolling over to another.
