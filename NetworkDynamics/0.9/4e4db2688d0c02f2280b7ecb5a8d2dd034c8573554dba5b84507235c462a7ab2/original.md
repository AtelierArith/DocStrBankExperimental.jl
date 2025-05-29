```
FeedForward <: FeedForwardType
```

Trait for component output functions `g` that have feed forward behavior. May depend on everything:

```
g!(outs..., x, ins..., p, t)
```

See also [`PureFeedForward`](@ref), [`NoFeedForward`](@ref) and [`PureStateMap`](@ref).
