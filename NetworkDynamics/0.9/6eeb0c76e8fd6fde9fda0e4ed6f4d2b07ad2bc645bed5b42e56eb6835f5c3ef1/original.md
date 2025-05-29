```
NoFeedForward <: FeedForwardType
```

Trait for component output functions `g` that have no feed forward behavior (do not depend on inputs):

```
g!(outs..., x, p, t)
```

See also [`PureFeedForward`](@ref), [`FeedForward`](@ref) and [`PureStateMap`](@ref).
