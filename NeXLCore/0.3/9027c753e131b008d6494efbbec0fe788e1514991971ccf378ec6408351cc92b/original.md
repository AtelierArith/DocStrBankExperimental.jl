```
obystoichiometry(elms::Pair{Element, <:AbstractFloat}..., valences = NeXLCore.defaultValences)
obystoichiometry(elms::Dict{Element, <:AbstractFloat}; valences = NeXLCore.defaultValences)
```

Compute O-by-stoichiometry from the provided mass fractions of elements.

Example:

```
obystoichiometry(n"Mg"=>0.1099, n"Al"=>0.0443, n"Si"=>0.1941, n"Ca"=>0.1034, n"Fe"=>0.0756)
0.39582340257233467
```
