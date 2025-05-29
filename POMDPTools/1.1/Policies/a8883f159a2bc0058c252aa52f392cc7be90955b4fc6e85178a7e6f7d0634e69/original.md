```
showpolicy([io], [mime], m::MDP, p::Policy)
showpolicy([io], [mime], statelist::AbstractVector, p::Policy)
showpolicy(...; pre=" ")
```

Print the states in `m` or `statelist` and the actions from policy `p` corresponding to those states.

For the MDP version, if `io[:limit]` is `true`, will only print enough states to fill the display.
