```julia
se(pp)

```

[`PersonParameter`](@ref) 推定値 `pp` から標準誤差を抽出します。

## 例

```jldoctest
julia> pp = PersonParameter(0.5, 0.3);

julia> se(pp)
0.3
```
