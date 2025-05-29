```
representation_matrix(x::AlgAssRelOrdElem, action::Symbol = :left) -> MatElem
```

Returns a matrix representing multiplication with $x$ with respect to the basis of `order(x)`. The multiplication is from the left if `action == :left` and from the right if `action == :right`.
