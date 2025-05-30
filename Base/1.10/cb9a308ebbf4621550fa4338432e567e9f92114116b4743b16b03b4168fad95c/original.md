```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)` returns the nearest integral value of the same type as `x` whose absolute value is less than or equal to the absolute value of `x`.

`trunc(T, x)` converts the result to type `T`, throwing an `InexactError` if the value is not representable.

Keywords `digits`, `sigdigits` and `base` work as for [`round`](@ref).

See also: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# Examples

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
