```
AppliedOperation
```

An abstract base class for already applied operations. An applied operation can be reversed iff it is the last applied operation on the DAG. Every applied operation stores a [`Diff`](@ref) from when it was initially applied to be able to revert the operation.

See also: [`revert_operation!`](@ref).
