```julia
chi_function_fourier(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Integer,
    n::Integer
) -> Any

```

The `n`th chi function at angular momentum `l` evaulated at reciprocal-space point `q`.

```julia
chi_function_fourier(psp, l, n; tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl:142`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl).

```julia
chi_function_fourier(psp, l, n)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:248`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl).
