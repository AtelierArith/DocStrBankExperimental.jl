```
rotation([T=Float64], θ)
```

与えられた角度 `θ`（ラジアン）で回転行列を生成します。これは、偏光成分の軸を任意に回転させるために使用できます。便利なことに、[`rotate`](@ref) メソッドは、この行列を生成することなく、成分を回転させます。

# 例

線形偏光子を90度反時計回りに回転させる

```jldoctest
julia> M = linear_polarizer();

julia> r = rotation(π/4);

julia> Mr = r' * M * r;

julia> Mr ≈ linear_polarizer(π/4)
true
```

# 参照

[`rotate`](@ref)
