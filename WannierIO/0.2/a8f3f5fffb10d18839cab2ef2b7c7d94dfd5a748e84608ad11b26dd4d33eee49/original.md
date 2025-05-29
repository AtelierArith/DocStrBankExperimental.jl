```julia
write_w90_wsvec(
    filename;
    Rvectors,
    n_wann,
    Tvectors,
    Tdegens,
    header
)

```

Write `prefix_wsvec.dat`.

# Keyword Arguments

  * `n_wann`: for Wigner-Seitz Rvectors, needs to provide a `n_wann` for number of   Wannier functions; for MDRS Rvectors, the `n_wann` is optional and can be   automatically determined from the `Tvectors`
  * `Tvectors` and `Tdegens`: if provided, write in MDRS format; otherwise, write in   Wigner-Seitz format

Also see the return values of [`read_w90_wsvec`](@ref).
