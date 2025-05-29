```
PureFeedForward <: FeedForwardType
```

Trait for component output functions `g` that have pure feed forward behavior (do not depend on x):

```
g!(outs..., ins..., p, t)
```

See also [`FeedForward`](@ref), [`NoFeedForward`](@ref) and [`PureStateMap`](@ref).
