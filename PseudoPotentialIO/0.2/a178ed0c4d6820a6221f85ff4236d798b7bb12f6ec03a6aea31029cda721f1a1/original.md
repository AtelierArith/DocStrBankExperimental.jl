```julia
projector_fourier(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Integer,
    n::Integer
) -> Any

```

The `n`th nonlocal Kleinman-Bylander projector at angular momentum `l` evaluated at reciprocal-space point `q`.

```julia
projector_fourier(psp, l, n)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl:144`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl).

```julia
projector_fourier(psp, l, n; tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl:137`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl).

```julia
projector_fourier(psp, l, n)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:240`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl).
