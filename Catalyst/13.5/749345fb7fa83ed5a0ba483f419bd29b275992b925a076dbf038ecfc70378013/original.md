```
addreaction!(network::ReactionSystem, rx::Reaction)
```

Add the passed in reaction to the [`ReactionSystem`](@ref). Returns the integer id of `rx` in the list of `Reaction`s within `network`.

Notes:

  * Any new species or parameters used in `rx` should be separately added to   `network` using [`addspecies!`](@ref) and [`addparam!`](@ref).
