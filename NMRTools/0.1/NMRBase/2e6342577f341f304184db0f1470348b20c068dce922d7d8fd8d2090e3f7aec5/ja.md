```
spin(n::Nucleus)
```

核 `n` のスピン量子数を返します。定義されていない場合は `nothing` を返します。

# 例

```jldoctest
julia> spin(H1)
1//2
```

関連項目は [`Coherence`](@ref) を参照してください。
