```
automaton_constructor(Σ::AbstractVector{<:AbstractMatrix})
```

Generates an automaton tracking admissible transitions between states. `Σ` is a  vector of matrices corresponding to a TAR model, assuming a default order generated  by [`perms`](@ref).

```
automaton_constructor(Σ::AbstractVector{<:AbstractMatrix}, seqlist)
```

Generates an automaton tracking admissible transitions between states given a custom list  of regime sequences.
