```
generate_buffer_validator(name::Symbol, regexp::RE; goto=true; docstring=true)
```

Generate code that, when evaluated, defines a function named `name`, which takes a single argument `data`, interpreted as a sequence of bytes. The function returns `nothing` if `data` matches `Machine`, else the index of the first invalid byte. If the machine reached unexpected EOF, returns `0`.

If `goto`, the function uses the faster but more complicated `:goto` code.
If `docstring`, automatically create a docstring for the generated function.

See also: [`generate_io_validator`](@ref)
