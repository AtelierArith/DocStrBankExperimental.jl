```
apply(b::Basis, u::AbstractVector; nelem=1, tmode=NOTRANSPOSE, emode=EVAL_INTERP)
```

Performs the same function as the above-defined [`apply!`](@ref apply!(b::Basis, nelem, tmode::TransposeMode, emode::EvalMode, u::AbstractCeedVector, v::AbstractCeedVector)), but automatically convert from Julia arrays to [`CeedVector`](@ref) for convenience.

The result will be returned in a newly allocated array of the correct size.
