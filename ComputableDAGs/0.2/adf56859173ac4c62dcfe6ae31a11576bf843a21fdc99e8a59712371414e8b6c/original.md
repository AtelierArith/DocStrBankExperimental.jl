```
DAG
```

The representation of the graph as a set of [`Node`](@ref)s.

[`Operation`](@ref)s can be applied on it using [`push_operation!`](@ref) and reverted using [`pop_operation!`](@ref) like a stack. To get the set of possible operations, use [`get_operations`](@ref). The members of the object should not be manually accessed, instead always use the provided interface functions.
