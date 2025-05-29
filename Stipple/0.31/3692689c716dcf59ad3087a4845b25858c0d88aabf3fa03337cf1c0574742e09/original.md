```
unsynchronize!(o::AbstractObservable, o_sync::Union{AbstractObservable, Nothing} = nothing)
```

Remove synchronization of observables.

### Parameters

  * `o::AbstractObservable`: The observable to unsynchronize.
  * `o_sync::Union{AbstractObservable, Nothing}`: The observable to unsynchronize with, if `nothing` (default) remove all bidirectional synchronizations and all unidirectional synchronizations from `o`, if `o_sync` is passed, remove all synchronizations between `o` and `o_sync`.

### Example 1

```
o = Observable(0)
on(o -> println("o: $o"), o)
o1 = Observable(1)
on(o1 -> println("o1: $o1"), o)
o2 = Observable(2)
on(o2 -> println("o2: $o2"), o)
o3 = Observable(3)

synchronize!(o1, o)
synchronize!(o2, o)
synchronize!(o3, o, biderectional = false)

# unsync o2 only
unsynchronize!(o2)

# wrong way of unsyncing o3, because it's unidirectional
unsynchronize!(o3)

# correct way of unsyncing o3
unsynchronize!(o3, o)

# unsync all syncs from o
unsynchronize!(o)
```
