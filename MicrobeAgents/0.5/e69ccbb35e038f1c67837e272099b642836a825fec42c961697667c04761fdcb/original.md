```
microbe_pathfinder_step!(microbe, model)
```

Identical to `microbe_step!` except that motion is constrained by the pathfinder (`model.pathfinder`) which defines inaccessible regions of space.
