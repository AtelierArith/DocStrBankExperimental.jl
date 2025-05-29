```
pow(x, y)
```

Compute the power of the positive real part of `x` by `y`. In particular, even if `y` is a thin integer, this is not equivalent to `pown(x, sup(y))`.

Implement the `pow` function of the IEEE Standard 1788-2015 (Table 9.1).

See also: [`fastpow`](@ref), [`pown`](@ref) and [`fastpown`](@ref).

# Examples

```jldoctest
julia> setdisplay(:full);

julia> pow(bareinterval(2, 3), bareinterval(2))
BareInterval{Float64}(4.0, 9.0)

julia> pow(interval(-1, 1), interval(3))
Interval{Float64}(0.0, 1.0, trv)

julia> pow(interval(-1, 1), interval(-3))
Interval{Float64}(1.0, Inf, trv)
```
