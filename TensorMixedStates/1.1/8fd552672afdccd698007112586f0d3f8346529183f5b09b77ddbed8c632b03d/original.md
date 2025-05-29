```
random_state(Pure()|Mixed(), ::System, linkdims::Int)
random_state(Pure()|Mixed(), ::Int, ::AbstractSite, linkdims::Int)
random_state(Pure()|Mixed(), ::Vector{<:AbstractSite}, linkdims::Int)
random_state(Pure()|Mixed(), ::State, linkdims::Int)
```

Return a random state, with the specified link dimension. If a State is given, randomize the given state.
