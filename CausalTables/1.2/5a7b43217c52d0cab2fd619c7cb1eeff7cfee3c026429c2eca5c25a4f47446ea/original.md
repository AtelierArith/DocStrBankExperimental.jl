```
confoundernames(o::CausalTable)
```

Outputs the confounder names of each response-treatment pair from the given `CausalTable` object.

# Arguments

  * `o::CausalTable`: The `CausalTable` object from which to extract the confounder names of each treatment-response pair.

# Returns

A matrix of Vectors containing the confounder names of each treatment-response pair.
