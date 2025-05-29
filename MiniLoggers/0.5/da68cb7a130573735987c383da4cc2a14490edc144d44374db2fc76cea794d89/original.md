```
JsonLogger(; <keyword arguments>)
```

JsonLogger constructor creates custom logger with json output, which can be used with usual `@info`, `@debug` commands. Supported keyword arguments include:

  * `io` (default `stdout`): IO stream which is used to output log messages below `errlevel` level. Can be either `IO` or `String`, in the latter case it is treated as a name of the output file.
  * `ioerr` (default `stderr`): IO stream which is used to output log messages above `errlevel` level. Can be either `IO` or `String`, in the latter case it is treated as a name of the output file.
  * `errlevel` (default `Error`): determines which output IO to use for log messages. If you want for all messages to go to `io`, set this parameter to `MiniLoggers.AboveMaxLevel`. If you want for all messages to go to `ioerr`, set this parameter to `MiniLoggers.BelowMinLevel`.
  * `minlevel` (default: `Info`): messages below this level are ignored. For example with default setting `@debug "foo"` is ignored.
  * `append` (default: `false`): defines whether to append to output stream or to truncate file initially. Used only if `io` or `ioerr` is a file path.
  * `flush` (default: `true`): whether to `flush` IO stream for each log message. Flush behaviour also affected by `flush_threshold` argument.
  * `squash_delimiter`: (default: "\t"): defines which delimiter to use when squashing multilines messages.
  * `flush_threshold::Union{Integer, TimePeriod}` (default: 0): if this argument is nonzero and `flush` is `true`, then `io` is flushed only once per `flush_threshold` milliseconds. I.e. if time between two consecutive log messages is less then `flush_threshold`, then second message is not flushed and will have to wait for the next log event.
  * `dtformat` (default: "yyyy-mm-dd HH:MM:SS"): if `datetime` parameter is used in `format` argument, this dateformat is applied for output timestamps.
  * `levelname` (default `string`): allows to redefine output of log level names. Should be function of the form `levelname(level::LogLevel)::String`
  * `format`: defines which keywords should be used in the output. If defined, should be a string which defines the structure of the output json. It should use keywords, and allowed keywords are:

      * `timestamp`: timestamp of the log message
      * `level`: name of log level (Debug, Info, etc)
      * `filepath`: filepath of the file, which produced log message
      * `basename`: basename of the filepath of the file, which produced log message
      * `line`: line number of the log command in the file, which produced log message
      * `group`: log group
      * `module`: name of the module, which contains log command
      * `id`: log message id
      * `message`: message itself

Format string should consists of comma separated tokens. In it's simplest form, tokens can be just keywords, then names of the keywords are used as a fieldnames. So, for example `"timestamp,level,message"` result in `{"timestamp":"2023-01-01 12:34:56","level":"Debug","message":"some logging message"}`. If fields must be renamed, then one should use `<field name>:<keyword>` form. For example, `"severity:level"` result in `{"severity":"Debug"}`, here field name is `severity` and the value is taken from the logging `level`. One can also create nested json, in order to do it one should use `<field name>:{<format string>}` form, where previous rules for format string also applies. For example, `source:{line, file:basename}` result in `{"source":{"line":123,"file":"calculations.jl"}}`

By default, `format` is `timestamp,level,basename,line,message`.
