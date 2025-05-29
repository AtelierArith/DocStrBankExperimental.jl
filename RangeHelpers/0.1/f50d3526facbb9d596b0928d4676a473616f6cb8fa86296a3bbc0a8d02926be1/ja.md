```
asrange(itr; check=true, atol, rtol)::AbstractRange
```

`itr`を範囲に変換し、結果をオプションで検証します。

```jldoctest
julia> using RangeHelpers

julia> asrange([1,2,3.0])
1.0:1.0:3.0

julia> asrange([1,2,3])
1:1:3

julia> asrange(1:3)
1:3

julia> asrange([1,2,4.0])
ERROR: ArgumentError: `itr`から範囲を構築できません
itr = [1.0, 2.0, 4.0]
[...]

julia> asrange([1,2,4.0], atol=10)
1.0:1.5:4.0
```
