```
numreactionparams(network)
```

Return the total number of parameters within the given [`ReactionSystem`](@ref) and subsystems that are `ReactionSystem`s.

Notes

  * If there are no subsystems this will be fast.
  * As this calls [`reactionparams`](@ref), it can be slow and will allocate if there are any subsystems.
