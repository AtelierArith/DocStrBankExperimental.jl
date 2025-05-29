```
MiniLogger(; <keyword arguments>)
```

MiniLogger constructor creates custom logger which can be used with usual `@info`, `@debug` commands.

Supported keyword arguments include:

  * `io` (default `stdout`): IO stream which is used to output log messages below `errlevel` level. Can be either `IO` or `String`, in the latter case it is treated as a name of the output file.
  * `ioerr` (default `stderr`): IO stream which is used to output log messages above `errlevel` level. Can be either `IO` or `String`, in the latter case it is treated as a name of the output file.
  * `errlevel` (default `Error`): determines which output IO to use for log messages. If you want for all messages to go to `io`, set this parameter to `MiniLoggers.AboveMaxLevel`. If you want for all messages to go to `ioerr`, set this parameter to `MiniLoggers.BelowMinLevel`.
  * `minlevel` (default: `Info`): messages below this level are ignored. For example with default setting `@debug "foo"` is ignored.
  * `append` (default: `false`): defines whether to append to output stream or to truncate file initially. Used only if `io` or `ioerr` is a file path.
  * `message_mode` (default: `:squash`): choose how message is transformed before being printed out. Following modes are supported:

      * `:notransformations`: message printed out as is, without any extra transformations
      * `:squash`: message is squashed to a single line, i.e. all `\n` are changed to `squash_delimiter` and `\r` are removed.
      * `:fullsquash`: all messages including error stacktraces are squashed to a single line, i.e. all `\n` are changed to `squash_delimiter` and `\r` are removed
      * `:markdown`: message is treated as if it is written in markdown
  * `squash_delimiter`: (default: "\t"): defines which delimiter to use in squash mode.
  * `flush` (default: `true`): whether to `flush` IO stream for each log message. Flush behaviour also affected by `flush_threshold` argument.
  * `flush_threshold::Union{Integer, TimePeriod}` (default: 0): if this argument is nonzero and `flush` is `true`, then `io` is flushed only once per `flush_threshold` milliseconds. I.e. if time between two consecutive log messages is less then `flush_threshold`, then second message is not flushed and will have to wait for the next log event.
  * `dtformat` (default: "yyyy-mm-dd HH:MM:SS"): if `datetime` parameter is used in `format` argument, this dateformat is applied for output timestamps.
  * `levelname` (default `string`): allows to redefine output of log level names. Should be function of the form `levelname(level::LogLevel)::String`
  * `format` (default: "[{timestamp:func}] {level:func}: {message}"): format for output log message. It accepts following keywords, which should be provided in curly brackets:

      * `timestamp`: timestamp of the log message
      * `level`: name of log level (Debug, Info, etc)
      * `filepath`: filepath of the file, which produced log message
      * `basename`: basename of the filepath of the file, which produced log message
      * `line`: line number of the log command in the file, which produced log message
      * `group`: log group
      * `module`: name of the module, which contains log command
      * `id`: log message id
      * `message`: message itself

Each keyword accepts color information, which should be added after colon inside curly brackets. Colors can be either from `Base.text_colors` or special keyword `func`, in which case is used automated coloring. Additionaly, `bold` modifier is accepted by the `format` argument. For example: `{line:red}`, `{module:cyan:bold}`, `{group:func}` are all valid parts of the format command.

Colour information is applied recursively without override, so `{{line} {module:cyan} {group}:red}` is equivalent to `{line:red} {module:cyan} {group:red}`.

If part of the format is not a recognised keyword, then it is just used as is, for example `{foo:red}` means that output log message contain word "foo" printed in red.
