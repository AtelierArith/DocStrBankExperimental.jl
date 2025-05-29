```
@scanf([io:Union{IO,String}, ], "%Fmt", args::...)
```

Scan input stream or string of using C `scanf` style format specification string and assign values to arguments.

The format string (not a variable) is analyzed at macro expansion time. Equivalent to `scanf(io, Scanf.format"%Fmt", args...)`.

# Examples

```jldoctest
r, a... = @scanf("%f%f%f%f", zeros(4)...)

julia> r, a, b = @scanf "23.4 text" "%f %2s" Float64 String
(2, 23.4, "te")
```
