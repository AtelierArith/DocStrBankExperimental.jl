```
TrackWatcher{K,T}()
```

This Watcher doesn't sample. It records everything enabled. You can iterate over enabled clocks with a for-loop. If we think of the model as providing changes in which transitions are enabled or disabled, this Watcher accumulates those changes to provide a consistent list of all enabled transitions. Together, a model and this Watcher provide the Semi-Markov core matrix, or the row of it that is currently known.

```julia
for entry in tracker
    entry.clock
    entry.distribution
    entry.te
    entry.when
end
```
