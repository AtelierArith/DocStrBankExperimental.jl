```
CustomParser(f, T)
```

Provide a custom parsing mechanism.

# Arguments:

  * `f`: the parser function
  * `T`: The type of the parsed value

The parser function must take the following arguments:

  * `str`: the entire string being parsed
  * `pos`: the position in the string at which to start parsing
  * `len`: the length of the string the maximum position where to parse till
  * `opts`: a [LocalOpts](@ref) object with options local to the current field.

The parser function must return a tuple of two values:

  * `result`: A `Nullable{T}`. Set to `Nothing{T}()` if parsing must fail, containing the value otherwise.
  * `nextpos`: If parsing succeeded this must be the next position after parsing finished, if it failed this must be the position at which parsing failed.
