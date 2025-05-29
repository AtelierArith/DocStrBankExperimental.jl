```
setebc!(self::F, fenids::AbstractVector{IT})  where {IT<:Integer}
```

Set the EBCs (essential boundary conditions).

Suppress all degrees of freedom at the given nodes.

`fenids`         - array of N node identifiers

Note:  Any call to `setebc!()` potentially changes the current assignment which degrees of freedom are free and which are fixed and therefore is presumed to invalidate the current degree-of-freedom numbering.
