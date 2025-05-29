```
dual(V::VectorSpace) -> VectorSpace
```

Return the dual space of `V`; also obtained via `V'`. This should satisfy `dual(dual(V)) == V`. It is assumed that `typeof(V) == typeof(V')`.
