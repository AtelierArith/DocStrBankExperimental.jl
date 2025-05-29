```
PseudoSet(;name   ::String,
           dir    ::String,
           pseudos::Dict)
```

Represents a set of pseudopotentials located in the `dir` directory. Can be loaded with `load(<server>, PseudoSet("name"))`, after having configured it with [`configure_pseudoset`](@ref).
