```
cut2sph(cut::Cut; keywords...) -> sph::SPHQPartition

cut2sph(cuts::AbstractVector{Cut}; keywords...) -> sphs::Vector{SPHQPartition}

cut2sph(cutfile::AbstractString; kwargs...) -> s::SPHQPartition
```

Convert a `Cut` object to a `SPHQPartition` using recursive FFT/IFFT methods from the Hansen 1988 book "Spherical Near-Field Antenna Measurements.

The single positional input argument can be either a string containing the name  of a Ticra-compatible, spherical polar cut file, or the returned value of type `Cut`  (or a vector of `Cut` objects) that results from reading such a file with `read_cutfile`.   The output of this function can be passed to `write_sphfile` to create a Ticra-compatible  file of Q-type spherical wave coefficients. If the input cut contains 3 polarization slots, the third slot will be discarded before performing the transformation.

If the input cuts extend in θ only to θ₀ < 180°, then it will be assumed that the fields are identically zero for θ₀ < θ ≤ 180°.

## Keyword Arguments (and their default values)

  * `mmax=1000`: An upper limit for the `m` (azimuthal) mode index to be included. The actual limit will be set to `min(Nϕ÷2, mmax)` for odd `Nϕ`, and `min(Nϕ÷2-1, mmax)` for even `Nϕ`, where `Nϕ` is the number of ϕ = constant polar cuts in the cut object.
  * `nmax=1000`: An upper limit for the `n` (polar) mode index to be included. The actual limit will be the lesser of `nmax` and `Nθ-1` where `Nθ` is the number of  θ values included in each ϕ = constant polar cut.
  * `pwrtol=0.0`: The power tolerance.  Spherical modes are included until the excluded modes' power is less than `pwrtol` times the total modal power.  A zero or negative value precludes removal of any modes.
