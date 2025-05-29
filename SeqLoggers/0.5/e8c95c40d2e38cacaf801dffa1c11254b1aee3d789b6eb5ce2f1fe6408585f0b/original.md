```
AdvancedFileLogger(
    dir::AbstractString, 
    file_name_pattern::AbstractString;
    log_format_function::Function=print_standard_format,
    min_level=Logging.Info
)
```

Return an file logger with extra functionality (in contrast to a `FileLogger` which is only a interface to `SimpleLogger`).

### Parameters

  * `dir` – log file directory
  * `file_name_pattern` – file name pattern for rotating log files (e.g. `raw"\a\c\c\e\s\s-YYYY-mm-dd-HH-MM.\l\o\g")`)
  * `log_format_function` – optional, default=`print_standard_format`
  * `min_level` – optional, default=`Logging.Info`

### Features

  * Define a `DateFormat`/`String` file pattern for rotating log messages to a new file → argument `file_name_pattern`
  * Provide a custom formatting function for writting to log files → argument `log_format_function`

### Returns

A `MinLevelLogger` which includes a `DatetimeRotatingFileLogger`.
