```
setebc!(self::F, fenid::IT) where {IT<:Integer}
```

Set the EBCs (essential boundary conditions).

Suppress all degrees of freedom at the given node.

`fenid` - One integer as a node identifier

All degrees of freedom at the node are set to zero.

Note:  Any call to `setebc!()` potentially changes the current assignment which degrees of freedom are free and which are fixed and therefore is presumed to invalidate the current degree-of-freedom numbering.
