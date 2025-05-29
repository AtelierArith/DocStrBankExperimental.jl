```
hangup_kick(;v=0.2, χ=0.99, θ=deg2rad(50.98), ϕ=deg2rad(30.0), PNOrder=typemax(Int))
hangup_kick(;v=0.2, chi=0.99, theta=deg2rad(50.98), phi=deg2rad(30.0), PNOrder=typemax(Int))
```

Construct a black-hole binary in [hangup-kick](https://arxiv.org/abs/1908.04382) configuration.

The spin magnitudes are both equal to `χ`.  The direction of $\vec{\chi}_1$ is given by the spherical coordinates (`θ`, `ϕ`).  $\vec{\chi}_2$ is the same, except that its projection into the orbital plane is opposite to that of $\vec{\chi}_1$.

See also [`superkick`](@ref) for the original systems, which can't actually achieve recoil kicks as large as those achieved by "hangup-kick" systems.

The physical mechanism here is similar to the one described in [`superkick`](@ref), with an additional "hangup" due to the fact that the spins have components parallel to the orbital angular velocity.  The physical interpretation of that part is that any system with such spin components will not merge as quickly because the remnant black hole must have total dimensionless spin less than 1, so excess angular momentum must be radiated away.  This gives the hangup-kick configuration more time to develop a large recoil.

# Examples

```julia-repl
julia> pnsystem = hangup_kick(v=0.1)
BBH{Vector{Float64}, 9223372036854775805//2}([0.5, 0.5, 0.3845784887294712, 0.6661094819774992, 0.6232957115416596, -0.3845784887294712, -0.6661094819774992, 0.6232957115416596, 1.0, 0.0, 0.0, 0.0, 0.1, 0.0])

julia> inspiral = orbital_evolution(pnsystem);

julia> inspiral[:v, 1]
0.1

julia> absvec(PostNewtonian.χ⃗₁(inspiral[1]))
0.99
```
