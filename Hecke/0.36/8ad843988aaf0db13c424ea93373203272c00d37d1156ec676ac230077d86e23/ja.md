```
inner_product(V::AbstractSpace, v::MatElem, w::MatElem) -> MatElem
```

`v * gram_matrix(V) * adjoint(w)` のショートカットです。
