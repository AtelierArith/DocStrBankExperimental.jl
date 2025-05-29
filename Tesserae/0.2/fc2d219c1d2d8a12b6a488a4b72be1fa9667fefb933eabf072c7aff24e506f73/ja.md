```
@P2G grid=>i particles=>p mpvalues=>ip [space] begin
    equations...
end
```

粒子からグリッドへの転送マクロ。`parent => index` の式に基づいて、`equations` 内の `a[index]` は `parent.a[index]` に変換されます。この `index` は他の名前に置き換えることができます。

# 例

```julia
@P2G grid=>i particles=>p mpvalues=>ip begin

    # 粒子からグリッドへの転送
    m[i]  = @∑ w[ip] * m[p]
    mv[i] = @∑ w[ip] * m[p] * v[p]
    f[i]  = @∑ -V[p] * σ[p] ⋅ ∇w[ip]

    # グリッド上の計算
    vⁿ[i] = mv[i] / m[i]
    v[i]  = vⁿ[i] + (f[i] / m[i]) * Δt

end
```

これはおおよそ以下のコードに展開されます：

```julia
# グリッドのプロパティをリセット
@. grid.m  = zero(grid.m)
@. grid.mv = zero(grid.mv)
@. grid.f  = zero(grid.f)

# 粒子からグリッドへの転送
for p in eachindex(particles)
    mp = mpvalues[p]
    nodeindices = neighboringnodes(mp)
    for ip in eachindex(nodeindices)
        i = nodeindices[ip]
        grid.m [i] += mp.w[ip] * particles.m[p]
        grid.mv[i] += mp.w[ip] * particles.m[p] * particles.v[p]
        grid.mv[i] += -particles.V[p] * particles.σ[p] ⋅ mp.∇w[ip]
    end
end

# グリッド上の計算
@. grid.vⁿ = grid.mv / grid.m
@. grid.v  = grid.vⁿ + (grid.f / grid.m) * Δt
```

!!! warning
    `@P2G` では、`グリッド上の計算` 部分は `粒子からグリッドへの転送` 部分の後に配置する必要があります。

