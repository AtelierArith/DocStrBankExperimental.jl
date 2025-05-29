```
quaternion(θ, n::Vec; normalize = true)
```

Construct `Quaternion` from angle `θ` and axis `n` as

$$
q = \cos\frac{\theta}{2} + \bm{n} \sin\frac{\theta}{2}
$$

The constructed quaternion is normalized such as `norm(q) ≈ 1` by default.

# Examples

```jldoctest
julia> q = quaternion(π/4, Vec(0,0,1))
0.9238795325112867 + 0.0𝙞 + 0.0𝙟 + 0.3826834323650898𝙠

julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> (q * x / q).vector ≈ rotmatz(π/4) * x
true
```
