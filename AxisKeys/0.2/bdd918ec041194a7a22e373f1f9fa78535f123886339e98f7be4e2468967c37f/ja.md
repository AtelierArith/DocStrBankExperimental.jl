```
named_axiskeys(arr)::NamedTuple
```

[`axiskeys`](@ref) とその名前を返します。重複した名前や名前のない軸がある場合、エラーがスローされます。

```jldoctest
julia> using AxisKeys

julia> arr = KeyedArray(rand(1,3), x=[1], y=[2,3,4]);

julia> named_axiskeys(arr)
(x = [1], y = [2, 3, 4])
```
