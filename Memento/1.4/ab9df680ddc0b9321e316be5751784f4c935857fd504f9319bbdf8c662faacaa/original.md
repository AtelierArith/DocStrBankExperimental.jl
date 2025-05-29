```
DefaultRecord <: AttributeRecord
```

Stores the most common logging event information. NOTE: if you'd like more logging attributes you can:

1. add them to DefaultRecord and open a pull request if the new attributes are applicable to most applications.
2. make a custom `Record` type.

# Fields

  * `date::Attribute{DateTime}`: timestamp of log event
  * `level::Attribute{AbstractString}`: log level
  * `levelnum::Attribute{Int}`: integer value for log level
  * `msg::Attribute{AbstractString}`: the log message itself
  * `name::Attribute{AbstractString}`: the name of the source logger
  * `pid::Attribute{Int}`: the pid of where the log event occured
  * `threadid::Attribute{Int}`: the thread id of where the log event occured
  * `lookup::Attribute{StackFrame}`: the top StackFrame
  * `stacktrace::Attribute{StackTrace}`: a stacktrace
