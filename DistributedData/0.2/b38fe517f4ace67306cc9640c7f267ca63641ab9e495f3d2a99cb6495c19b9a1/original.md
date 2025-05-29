```
save_at(worker, sym, val)
```

Saves value `val` to symbol `sym` at `worker`. `sym` should be quoted (or contain a symbol). `val` gets unquoted in the processing and evaluated at the worker, quote it if you want to pass exact command to the worker.

This is loosely based on the package ParallelDataTransfers, but made slightly more flexible by omitting/delaying the explicit fetches etc. In particular, `save_at` is roughly the same as `ParallelDataTransfers.sendto`, and `get_val_from` works very much like `ParallelDataTransfers.getfrom`.

# Return value

A future with Nothing that can be fetched to see that the operation has finished.

# Examples

```
addprocs(1)
save_at(2,:x,123)       # saves 123
save_at(2,:x,myid())    # saves 1
save_at(2,:x,:(myid())) # saves 2
save_at(2,:x,:(:x))     # saves the symbol :x
                        # (just :x won't work because of unquoting)
```

# Note: Symbol scope

The symbols are saved in Main module on the corresponding worker. For example, `save_at(1, :x, nothing)` *will* erase your local `x` variable. Beware of name collisions.
