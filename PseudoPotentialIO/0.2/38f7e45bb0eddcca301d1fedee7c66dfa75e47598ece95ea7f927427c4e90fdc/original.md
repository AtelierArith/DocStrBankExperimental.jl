```julia
pseudo_cutoff_radius(
    psp::PseudoPotentialIO.AbstractPsP;
    f,
    tol
) -> Any

```

Find the cutoff radius for the pseudopotential. Supply a function `f` to determine what kind of reduction over cutoff radii for different quantities is performed. Supply `tol` if you'd like to truncate the quantities where they decay to `|f| < tol`.

```julia
pseudo_cutoff_radius(psp; f, tol)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:389`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl).
