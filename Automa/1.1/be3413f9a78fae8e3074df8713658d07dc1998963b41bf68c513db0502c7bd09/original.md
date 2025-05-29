```
generate_io_validator(funcname::Symbol, regex::RE; goto::Bool=false)
```

**NOTE: This method requires TranscodingStreams to be loaded**

Create code that, when evaluated, defines a function named `funcname`. This function takes an `IO`, and checks if the data in the input conforms to the regex, without executing any actions. If the input conforms, return `nothing`. Else, return `(byte, (line, col))`, where `byte` is the first invalid byte, and `(line, col)` the 1-indexed position of that byte. If the invalid byte is a `\n` byte, `col` is 0 and the line number is incremented. If the input errors due to unexpected EOF, `byte` is `nothing`, and the line and column given is the last byte in the file.

If `goto`, the function uses the faster but more complicated `:goto` code.

See also: [`generate_buffer_validator`](@ref)
