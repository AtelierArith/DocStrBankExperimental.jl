```
treatmentparents(o::CausalTable)
```

Selects the parents of each treatment variable from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the parent variables of each treatment.
  * `collape_parents::Bool`: Optional parameter, whether to collapse the output to a single `CausalTable` object if there is either only one treatment or all treatments have the same parents. Defaults to `true`.

# Returns

A new `CausalTable` containing only the causes of the treatment (if a single treatment, or all treatments share the same set of causes); otherwise, a Vector of CausalTable objects containing the causes of each treatment.
