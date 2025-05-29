```
mutable struct ObserverFunction <: Function
```

Fields:

```
f::Function
observable::AbstractObservable
weak::Bool
```

`ObserverFunction` is intended as the return value for `on` because we can remove the created closure from `obsfunc.observable`'s listener vectors when ObserverFunction goes out of scope - as long as the `weak` flag is set. If the `weak` flag is not set, nothing happens when the ObserverFunction goes out of scope and it can be safely ignored. It can still be useful because it is easier to call `off(obsfunc)` instead of `off(observable, f)` to release the connection later.
