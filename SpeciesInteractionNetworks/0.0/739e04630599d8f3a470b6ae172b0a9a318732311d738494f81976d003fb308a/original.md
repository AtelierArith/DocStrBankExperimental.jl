```
PermutationConstraint
```

The `PermutationConstraint` specifies which structural constraint is enforced. It is defined as an abstract type, and the subtypes can be passed as the second argument to `swap!`.

Currently supported constraints are `Degree` (degree distribution is maintained), `Generality` (number of out-going links is maintained), `Vulnerability` (number of in-going links is maintained), and `Connectance` (only the connectance is maintained). Note that *in addition*, species cannot become disconnected, even if the constraint is not acting on the degree / degree distribution.
