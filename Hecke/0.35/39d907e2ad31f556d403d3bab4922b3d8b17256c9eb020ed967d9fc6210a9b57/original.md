```
inner_product(L::AbstractLat, v::Vector, w::Vector) -> FieldElem
```

Return the inner product of `v` and `w` with respect to the bilinear form of the `rational_span(L)`. In case $L$ is free and $G$ its gram matrix, this is $v G w^t$.
