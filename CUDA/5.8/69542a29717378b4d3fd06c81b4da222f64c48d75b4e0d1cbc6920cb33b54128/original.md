```
vote_uni_sync(mask::UInt32, predicate::Bool)
```

Evaluate `predicate` for all active threads of the warp and return whether `predicate` is the same for any of them.
