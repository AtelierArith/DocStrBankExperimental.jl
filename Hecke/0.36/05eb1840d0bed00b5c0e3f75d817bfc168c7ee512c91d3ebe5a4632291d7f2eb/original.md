```
representation_matrix(a::AbstractAssociativeAlgebraElem, action::Symbol = :left) -> MatElem
```

Returns a matrix over `base_ring(algebra(a))` representing multiplication with $a$ with respect to the basis of `algebra(a)`. The multiplication is from the left if `action == :left` and from the right if `action == :right`.
