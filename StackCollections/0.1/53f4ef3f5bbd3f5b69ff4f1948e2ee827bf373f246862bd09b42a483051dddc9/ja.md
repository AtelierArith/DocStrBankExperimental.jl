```
delete(s::AbstractStackSet, v::Int)
```

`v`を含まない`s`のコピーを返します。

# 例

```jldoctest
julia> s = DigitSet([4, 41, 9]);

julia> delete(s, 1)
DigitSet with 3 elements:
  4
  9
  41
```

関連項目: [`pop`](@ref)
