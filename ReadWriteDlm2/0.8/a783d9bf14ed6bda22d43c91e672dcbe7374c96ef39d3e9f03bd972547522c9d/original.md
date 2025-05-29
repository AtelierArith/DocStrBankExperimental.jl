```
readcsv2(source, T::Type=Any; opts...)
```

Equivalent to `readdlm2()` with delimiter `','` and `decimal='.'`. Default Type `Any` activates parsing of `Bool`, `Int`, `Float64`, `Complex`, `Rational`, `Missing`, `DateTime`, `Date` and `Time`.

# Code Example

```jldoctest
julia> using ReadWriteDlm2

julia> B = Any[1 complex(1.5,2.7);1.0 1//3];

julia> writecsv2("test.csv", B)

julia> readcsv2("test.csv")
2×2 Array{Any,2}:
 1    1.5+2.7im
 1.0    1//3
```
