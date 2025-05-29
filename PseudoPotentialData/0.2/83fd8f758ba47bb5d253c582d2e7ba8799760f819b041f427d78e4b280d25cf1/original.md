```julia
recommended_cutoff(
    family::PseudoPotentialData.PseudoFamily,
    element::Symbol
) -> NamedTuple{(:Ecut, :supersampling, :Ecut_density), <:Tuple{Union{Missing, Float64}, Union{Missing, Float64}, Union{Missing, Float64}}}

```

Return the recommended kinetic energy cutoff, supersampling and density cutoff for the pseudopotential indentified by this `family` and `element`. `Ecut` and `Ecut_density` are returned in Hartree.
