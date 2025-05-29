```
mw(formula::AbstractString, net_charge = 0)
mw(elements::Union{<: Vector{<: Pair}, <: Dictionaries.PairDictionary}, net_charge = 0)
mw(chemical::AbstractChemical)
```

Molecular weight of a formula, collection of elements pairs or chemical.

Molecular weight is referred to molecular or formula mass for single monoisotopic chemicals, and weighted average for multiple chemicals. 
