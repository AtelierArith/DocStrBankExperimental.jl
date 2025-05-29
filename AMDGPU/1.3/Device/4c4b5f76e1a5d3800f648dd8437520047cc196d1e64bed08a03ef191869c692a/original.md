```
sync_workgroup_count(predicate::Cint)::Cint
```

Identical to `sync_workgroup`, with the additional feature that it evaluates the predicate for all workitems in the workgroup and returns the number of workitems for which predicate evaluates to non-zero.
