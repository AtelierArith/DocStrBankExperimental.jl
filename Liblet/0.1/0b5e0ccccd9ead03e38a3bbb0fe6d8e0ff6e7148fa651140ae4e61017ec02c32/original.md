This type represents an [`Automaton`](@ref) transition. It has a `from` starting *state* and a `to` destination *state* and a `label`

```
Transition(from::Union{AbstractString, Iterable}, label::AbstractString, to::Union{AbstractString, Iterable})
```

Build a transition based on the given states.
