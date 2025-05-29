```
measurement(string) -> Measurement{Float64}
```

Parse the string and return a `Measurement{Float64}` object.

Examples of valid strings and the resulting `Measurement{Float64}` are:

```jldoctest
julia> using Measurements

julia> measurement("-123.4(56)")
-123.4 ± 5.6

julia> measurement("+1234(56)e-1")
123.4 ± 5.6

julia> measurement("12.34e-1 +- 0.56e1")
1.2 ± 5.6

julia> measurement("(-1.234 ± 0.056)e2")
-123.4 ± 5.6

julia> measurement("1234e-1 +/- 5.6e0")
123.4 ± 5.6

julia> measurement("-1234e-1")
-123.4 ± 0.0
```
