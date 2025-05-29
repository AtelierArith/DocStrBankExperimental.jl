```julia
projector_cutoff_radius(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Int64,
    n::Int64;
    tol
) -> Float64

```

Cutoff radius of the `n`th Kleinman-Bylander non-local projector at angular momentum `l` in real-space.

```julia
projector_cutoff_radius(, , ; tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl:60`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl).

```julia
projector_cutoff_radius(psp, l, n; tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl:72`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl).

```julia
projector_cutoff_radius(psp, l, n; tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:176`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl).
