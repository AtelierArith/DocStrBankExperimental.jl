```
set_log_path(path::String)
```

Specify the path that is used to save the log files. If the directory does not exist, it is created the first time a log file is written.

Must be called before [`create_simulation`](@ref). If this is not done, the log files are written to a subfolder `log` of the current working directory.
