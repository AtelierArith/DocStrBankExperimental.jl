```
@P2G grid=>i particles=>p mpvalues=>ip [space] begin
    equations...
end
```

Particle-to-grid transfer macro. Based on the `parent => index` expressions, `a[index]` in `equations` translates to `parent.a[index]`. This `index` can be replaced with any other name.

# Examples

```julia
@P2G grid=>i particles=>p mpvalues=>ip begin

    # Particle-to-grid transfer
    m[i]  = @∑ w[ip] * m[p]
    mv[i] = @∑ w[ip] * m[p] * v[p]
    f[i]  = @∑ -V[p] * σ[p] ⋅ ∇w[ip]

    # Calculation on grid
    vⁿ[i] = mv[i] / m[i]
    v[i]  = vⁿ[i] + (f[i] / m[i]) * Δt

end
```

This expands to roughly the following code:

```julia
# Reset grid properties
@. grid.m  = zero(grid.m)
@. grid.mv = zero(grid.mv)
@. grid.f  = zero(grid.f)

# Particle-to-grid transfer
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

# Calculation on grid
@. grid.vⁿ = grid.mv / grid.m
@. grid.v  = grid.vⁿ + (grid.f / grid.m) * Δt
```

!!! warning
    In `@P2G`, `Calculation on grid` part must be placed after `Particle-to-grid transfer` part.

