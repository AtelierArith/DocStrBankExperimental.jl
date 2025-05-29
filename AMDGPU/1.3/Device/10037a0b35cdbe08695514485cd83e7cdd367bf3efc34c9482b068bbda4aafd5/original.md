```
sync_workgroup_and(predicate::Cint)::Cint
```

Identical to `sync_workgroup`, with the additional feature that it evaluates the predicate for all workitems in the workgroup and returns non-zero if and only if predicate evaluates to non-zero for all of them.
