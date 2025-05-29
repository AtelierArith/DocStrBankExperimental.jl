```
named_axiskeys(arr)::NamedTuple
```

Return the [`axiskeys`](@ref) along with their names. If there are duplicate names or unnamed axes, an error is thrown.

```jldoctest
julia> using AxisKeys

julia> arr = KeyedArray(rand(1,3), x=[1], y=[2,3,4]);

julia> named_axiskeys(arr)
(x = [1], y = [2, 3, 4])
```
