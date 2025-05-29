```
pop(s::AbstractStackSet, v::Int)
```

`s`から`v`を除いたコピーを返します。`v`が`s`に存在しない場合は、エラーを発生させます。

# 例

```jldoctest
julia> s = DigitSet([4, 41, 9]);

julia> pop(s, 41)
DigitSet with 2 elements:
  4
  9
```

参照: [`delete`](@ref)
