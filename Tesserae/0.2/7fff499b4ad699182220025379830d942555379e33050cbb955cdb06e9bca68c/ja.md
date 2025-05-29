```
@G2P grid=>i particles=>p mpvalues=>ip begin
    equations...
end
```

グリッドから粒子への転送マクロ。`parent => index` の式に基づいて、`equations` 内の `a[index]` は `parent.a[index]` に変換されます。この `index` は他の名前に置き換えることができます。

# 例

```julia
@G2P grid=>i particles=>p mpvalues=>ip begin

    # グリッドから粒子への転送
    v[p] += @∑ w[ip] * (vⁿ[i] - v[i])
    ∇v[p] = @∑ v[i] ⊗ ∇w[ip]
    x[p] += @∑ w[ip] * v[i] * Δt

    # 粒子上の計算
    Δϵₚ = symmetric(∇v[p]) * Δt
    F[p]  = (I + ∇v[p]*Δt) ⋅ F[p]
    V[p]  = V⁰[p] * det(F[p])
    σ[p] += λ*tr(Δϵₚ)*I + 2μ*Δϵₚ # 線形弾性材料

end
```

これはおおよそ以下のコードに展開されます：

```julia
# グリッドから粒子への転送
for p in eachindex(particles)
    mp = mpvalues[p]
    nodeindices = neighboringnodes(mp)
    Δvₚ = zero(eltype(particles.v))
    ∇vₚ = zero(eltype(particles.∇v))
    Δxₚ = zero(eltype(particles.x))
    for ip in eachindex(nodeindices)
        i = nodeindices[ip]
        Δvₚ += mp.w[ip] * (grid.vⁿ[i] - grid.v[i])
        ∇vₚ += grid.v[i] ⊗ mp.∇w[ip]
        Δxₚ += mp.w[ip] * grid.v[i] * Δt
    end
    particles.v[p] += Δvₚ
    particles.∇v[p] = ∇vₚ
    particles.x[p] += Δxₚ
end

# 粒子上の計算
for p in eachindex(particles)
    Δϵₚ = symmetric(particles.∇v[p]) * Δt
    particles.F[p]  = (I + particles.∇v[p]*Δt) ⋅ particles.F[p]
    particles.V[p]  = particles.V⁰[p] * det(particles.F[p])
    particles.σ[p] += λ*tr(Δϵₚ)*I + 2μ*Δϵₚ # 線形弾性材料
end
```

!!! warning
    `@G2P` では、`粒子上の計算` 部分は `グリッドから粒子への転送` 部分の後に配置する必要があります。

