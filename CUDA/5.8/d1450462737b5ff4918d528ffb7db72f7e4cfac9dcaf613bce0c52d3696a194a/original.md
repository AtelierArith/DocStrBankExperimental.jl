```
vote_all_sync(mask::UInt32, predicate::Bool)
```

Evaluate `predicate` for all active threads of the warp and return whether `predicate` is true for all of them.
