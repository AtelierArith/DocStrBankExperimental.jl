```julia
value(pp)

```

[`PersonParameter`](@ref) 推定値 `pp` から値を抽出します。

## 例

```jldoctest
julia> pp = PersonParameter(0.0, 1.0);

julia> value(pp)
0.0
```
