```
instrumentsmatrix(o::CausalTable; collapse_parents = true)
```

Outputs the treatment-variable instruments from the given `CausalTable` object as a matrix (or matrix of matrices, if multiple treatment-response pairs are present).

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the instruments of each treatment-response pair.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `Matrix` object if there is either only one treatment-response pair or all pair share the same set of instruments. Defaults to `true`.

# Returns

A matrix containing only the confounders.
