```
@ncon(tensorlist, indexlist; order = ..., output = ...)
```

Contract the tensors in `tensorlist` (of type `Vector` or `Tuple`) according to the network as specified by `indexlist`. Here, `indexlist` is a list (i.e. a `Vector` or `Tuple`) with the same length as `tensorlist` whose entries are themselves lists (preferably `Vector{Int}`) where every integer entry provides a label for corresponding index/dimension of the corresponding tensor in `tensorlist`. Positive integers are used to label indices that need to be contracted, and such thus appear in two different entries within `indexlist`, whereas negative integers are used to label indices of the output tensor, and should appear only once.

By default, contractions are performed in the order such that the indices being contracted over are labelled by increasing integers, i.e. first the contraction corresponding to label `1` is performed. The output tensor had an index order corresponding to decreasing (negative, so increasing in absolute value) index labels. The keyword arguments `order` and `output` allow to change these defaults.

The advantage of the macro `@ncon` over the function call `ncon` is that, if `tensorlist` is not just some variable but an actual list (as a tuple with parentheses or a vector with square brackets) at the call site, the `@ncon` macro will scan for conjugation calls, e.g. `conj(A)`, and replace this with just `A` but build a matching list of conjugation flags to be specified to `ncon`. This makes it more convenient to specify tensor conjugation, without paying the cost of actively performing the conjugation beforehand.

See also the function [`ncon`](@ref).
