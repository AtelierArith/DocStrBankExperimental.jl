```
superkick(;v=0.2, χ=0.99, PNOrder=typemax(Int))
superkick(;v=0.2, chi=0.99, PNOrder=typemax(Int))
```

Construct a black-hole binary in "superkick" configuration.

This is the scenario first published by [Campanelli et al. (2007)](https://arxiv.org/abs/gr-qc/0701164), which has equal-mass black holes with spins of equal magnitude oriented in opposite directions in the orbital plane.  This configuration produces large asymmetrical emission of gravitational-wave linear momentum along the $+z$ or $-z$ directions, depending on which part of the orbit the binary is in.  Depending on when the system mergers, the remnant may then acquire a huge recoil velocity.

(That recoil velocity, of course, depends on details of the merger, which post-Newtonian approximations cannot describe.  Therefore, we cannot actually use PN methods to derive any useful information about the remnant.)

Note that the name "superkick" appeared in the literature before a class of systems that can achieve even larger recoil velocities: see [`hangup_kick`](@ref) for such systems.

# Examples

```julia-repl
julia> pnsystem = superkick(v=0.1)
BBH{Vector{Float64}, 9223372036854775805//2}([0.5, 0.5, 0.99, 0.0, 0.0, -0.99, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.1, 0.0])

julia> inspiral = orbital_evolution(pnsystem);

julia> inspiral[:v, 1]
0.1

julia> absvec(PostNewtonian.χ⃗₁(inspiral[1]))
0.99
```
