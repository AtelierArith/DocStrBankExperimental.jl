```
base(x::Option{T})
```

`Option{T}`を`Union{Some{T}, Nothing}`に変換します。

参照: [`Option`](@ref)

# 例

```jldoctest
julia> sub_nonneg(x::Int)::Option{Int} = x < 1 ? none : some(x - 1);

julia> base(sub_nonneg(-3)) === nothing
true

julia> base(sub_nonneg(2))
Some(1)
```
