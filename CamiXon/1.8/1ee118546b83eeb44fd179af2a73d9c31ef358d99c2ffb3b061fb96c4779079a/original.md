```
listIsotopes(Z1::Int, Z2::Int; fmt=Object)
listIsotopes(itr; fmt=Object)
```

All isotopes with atomic number in the range `itr = Z1:Z2`.

Output options: `Object` (default), `String`, `Latex`, `Info`.

#### Example:

```
julia> listIsotopes(1,3) == listIsotopes(1:3)
true

julia> listIsotopes(1:1; fmt=Object)
3-element Vector{Any}:
 Isotope("¹H", "hydrogen", 1, 1, 0, 0.8783, 1.007825032, 1//2, 1, 1.0e100, 2.792847351, 0.0, 99.9855)
 Isotope("²D", "deuterium", 1, 2, 1, 2.1421, 2.014101778, 1, 1, 1.0e100, 0.857438231, 0.0028578, 0.0145)
 Isotope("³T", "tritium", 1, 3, 2, 1.7591, 3.016049281, 1//2, 1, 12.33, 2.97896246, 0.0, nothing)
```
