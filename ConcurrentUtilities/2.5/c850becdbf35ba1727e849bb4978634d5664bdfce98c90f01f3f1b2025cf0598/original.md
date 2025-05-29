```
OrderedSynchronizer(i=1)
```

A threadsafe synchronizer that allows ensuring concurrent work is done in a specific order. The `OrderedSynchronizer` is initialized with an integer `i` that represents the current "order" of the synchronizer.

Work is "scheduled" by calling `put!(f, x, i)`, where `f` is a function that will be called like `f()` when the synchronizer is at order `i`, and will otherwise wait until other calls to `put!` have finished to bring the synchronizer's state to `i`. Once `f()` is called, the synchronizer's state is incremented by 1 and any waiting `put!` calls check to see if it's their turn to execute.

A synchronizer's state can be reset to a specific value (1 by default) by calling `reset!(x, i)`.
