```
none
```

`ResultConstructor{Nothing, Err}(nothing)`のシングルトンインスタンス。この値は、エラー値を与える任意の`Option{T}`に`convert`できるため、有用です。

参照: [`Option`](@ref)

# 例

```jldoctest
julia> f(x)::Option{Float64} = iszero(x) ? none : 1 / x;

julia> f(0)
none(Float64)

julia> struct MaybeInt32 x::Option{Int32} end;

julia> MaybeInt32(none)
MaybeInt32(none(Int32))
```
