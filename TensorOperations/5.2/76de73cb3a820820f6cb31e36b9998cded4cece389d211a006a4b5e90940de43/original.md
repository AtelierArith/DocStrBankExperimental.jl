```
ncon(tensorlist, indexlist, [conjlist, sym]; order = ..., output = ..., backend = ..., allocator = ...)
```

Contract the tensors in `tensorlist` (of type `Vector` or `Tuple`) according to the network as specified by `indexlist`. Here, `indexlist` is a list (i.e. a `Vector` or `Tuple`) with the same length as `tensorlist` whose entries are themselves lists (preferably `Vector{Int}`) where every integer entry provides a label for corresponding index/dimension of the corresponding tensor in `tensorlist`. Positive integers are used to label indices that need to be contracted, and such thus appear in two different entries within `indexlist`, whereas negative integers are used to label indices of the output tensor, and should appear only once.

Optional arguments in another list with the same length, `conjlist`, whose entries are of type `Bool` and indicate whether the corresponding tensor object should be conjugated (`true`) or not (`false`). The default is `false` for all entries.

By default, contractions are performed in the order such that the indices being contracted over are labelled by increasing integers, i.e. first the contraction corresponding to label `1` is performed. The output tensor had an index order corresponding to decreasing (negative, so increasing in absolute value) index labels. The keyword arguments `order` and `output` allow to change these defaults.

See also the macro version [`@ncon`](@ref).
