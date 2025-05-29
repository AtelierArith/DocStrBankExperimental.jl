```
value_map(ps::Vector,p0::Vector)
```

A Function to create parameter values for indexed Variables more convenient.

# Arguments

*`ps::Vector`: A vector of parameters, that have no value assigned to them. *`p0::Vector`: A vector for numeric values, that should get assigned to the corresponding     entry in the `ps` vector. For Single-Indexed Variables the entry in the vector can also be again     a Vector, that has an amount of entries as the index of the variables has range. For Double-Indexed     Variables, this can also be a Matrix of a dimension, that corresponds to the ranges of the indices     of the given variable.
