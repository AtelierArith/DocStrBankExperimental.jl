```
HallOfFame(options::AbstractOptions, dataset::Dataset{T,L}) where {T<:DATA_TYPE,L<:LOSS_TYPE}
```

Create empty HallOfFame. The HallOfFame stores a list of `PopMember` objects in `.members`, which is enumerated by size (i.e., `.members[1]` is the constant solution). `.exists` is used to determine whether the particular member has been instantiated or not.

Arguments:

  * `options`: AbstractOptions containing specification about deterministic.
  * `dataset`: Dataset containing the input data.
