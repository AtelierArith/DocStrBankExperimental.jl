```
inner_product(V::AbstractSpace, v::MatElem, w::MatElem) -> MatElem
```

Shortcut for `v * gram_matrix(V) * adjoint(w)`.
