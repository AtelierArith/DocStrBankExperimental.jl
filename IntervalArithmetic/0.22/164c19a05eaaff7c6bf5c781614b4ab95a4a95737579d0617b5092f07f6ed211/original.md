```
pown(x, n)
```

Implement the `pown` function of the IEEE Standard 1788-2015 (Table 9.1).

See also: [`fastpown`](@ref), [`pow`](@ref) and [`fastpow`](@ref).

# Examples

```jldoctest
julia> setdisplay(:full);

julia> pown(bareinterval(2, 3), 2)
BareInterval{Float64}(4.0, 9.0)

julia> pown(interval(-1, 1), 3)
Interval{Float64}(-1.0, 1.0, com)

julia> pown(interval(-1, 1), -3)
Interval{Float64}(-Inf, Inf, trv)
```
