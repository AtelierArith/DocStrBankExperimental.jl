`system` is the main elaboration/flattening function that returns an `ODESystem`.

```julia
system(a)
```

### Arguments

  * `a` : the input model containing a nested vector of equations

### Optional/Keyword Arguments

  * `simplify = true` : whether `structural_simplify` is used to simplify results

### Returns

  * `::ODESystem` : the flattened model
