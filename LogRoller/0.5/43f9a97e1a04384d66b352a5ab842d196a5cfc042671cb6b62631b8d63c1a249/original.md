RollingLogger(filename, sizelimit, nfiles, min*level=Info; timestamp*identifier::Symbol=:time, format::Symbol=:console) Log into a log file. Rotate log file based on file size. Compress rotated logs.

Logs can be formatted as JSON by setting the optional keyword argument `format` to `:json`. A JSON formatted log entry is a JSON object. It should have these keys (unless they are empty): The message part can contain the following keys unless they are empty:

  * `metadata`: event metadata e.g. timestamp, line, filename, ...
  * `message`: the log message string
  * `keywords`: any keywords provided
