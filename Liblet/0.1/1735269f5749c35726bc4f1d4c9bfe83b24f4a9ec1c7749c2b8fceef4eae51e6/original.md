```
possiblesteps(d::Derivation; prod::Union{Int, Nothing} = nothing, pos::Union{Int, Nothing} = nothing)
```

Returns all the possible steps that can be performed given the grammar and current *sentential form*.

Determines all the position of the *sentential form* that correspond to the left-hand side of one of the production in the grammar, returning the position and production number. If a production is specified, it yields only the pairs referring to it; similarly, if a position is specified, it yields only the pairs referring to it.
