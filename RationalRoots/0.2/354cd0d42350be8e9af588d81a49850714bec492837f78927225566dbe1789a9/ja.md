```
signedsquare(x)
```

返す `sign(x)*x*x = x*abs(x)`。もし `x` が `RationalRoot` の場合、適切な有理型を返す。

```jldoctest
julia> signedsquare(-2)
-4

julia> signedsquare(4.0)
16.0

julia> signedsquare(-RationalRoot{Int}(3//2))
-9//4
```
