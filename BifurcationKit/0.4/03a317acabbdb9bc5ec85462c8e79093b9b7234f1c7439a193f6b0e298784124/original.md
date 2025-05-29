```julia
get_normal_form(
    prob,
    br,
    id_bif;
    nev,
    verbose,
    ζs,
    lens,
    Teigvec,
    scaleζ,
    autodiff,
    δ,
    k...
)

```

Compute the normal form (NF) of periodic orbits. We detail the additional keyword arguments specific to periodic orbits

# Optional arguments

  * `prm = true` compute the normal form using Poincaré return map (PRM). If false, use the Iooss normal form.
  * `nev = length(eigenvalsfrombif(br, id_bif))`,
  * `verbose = false`,
  * `ζs = nothing`, pass the eigenvectors
  * `lens = getlens(br)`,
  * `Teigvec = _getvectortype(br)` type of the eigenvectors (can be useful for GPU)
  * `scaleζ = norm`, scale the eigenvector
  * `prm = true` NF based on Poincare return map (`prm=true`) or Iooss' method.
  * `autodiff = false` use autodiff or finite differences in some part of the normal form computation
  * `detailed = true` to get detailed normal form
  * `δ = getdelta(prob)` delta used for finite differences

# Notes

For collocation, the default method to compute the NF of Period-doubling and Neimark-Sacker bifurcations is Iooss' method.
