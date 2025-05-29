```
eigenspaces(M::MatElem{T}; side::Symbol = :left)
  where T <: FieldElem -> Dict{T, MatElem{T}}
```

Return a dictionary containing the eigenvalues of $M$ as keys and bases for the corresponding eigenspaces as values. If side is `:right`, the right eigenspaces are computed, if it is `:left` then the left eigenspaces are computed.

See also `eigenspace`.
