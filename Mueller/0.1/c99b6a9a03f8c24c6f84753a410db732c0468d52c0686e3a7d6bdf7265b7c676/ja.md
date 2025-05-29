```
rotate(M, θ)
```

ムーラー行列 `M` で表されるコンポーネントを角度 `θ`（ラジアン単位）だけ反時計回りに回転させます。

# 例

```jldoctest
julia> M = linear_polarizer();

julia> Mr = rotate(M, π/2);

julia> Mr ≈ linear_polarizer(π/2)
true
```

# 参照

[`Mueller.rotation`](@ref)
