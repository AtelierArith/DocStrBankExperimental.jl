```
vote_ballot_sync(mask::UInt32, predicate::Bool)
```

Evaluate `predicate` for all active threads of the warp and return an integer whose Nth bit is set if and only if `predicate` is true for the Nth thread of the warp and the Nth thread is active.
