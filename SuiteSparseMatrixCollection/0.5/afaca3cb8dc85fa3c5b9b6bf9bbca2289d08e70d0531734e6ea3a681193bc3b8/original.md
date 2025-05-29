```
manage_ssmc(; sort_by::Symbol=:name, rev::Bool=false)
```

Opens a prompt allowing the user to selectively remove matrices from the SuiteSparseMatrixCollection.

By default, the matrices are sorted by name. Alternatively, you can sort them by file size on disk by specifying `sort_by=:size`. Use `rev=true` to reverse the sort order.
