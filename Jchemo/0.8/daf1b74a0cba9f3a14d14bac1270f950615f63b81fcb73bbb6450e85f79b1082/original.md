```
transf(object::Interpl, X)
transf!(object::Interpl, X::Matrix, M::Matrix)
```

Compute the preprocessed data from a model.

  * `object` : Model.
  * `X` : X-data to transform.
  * `M` : Pre-allocated output matrix (n, p).

The in-place function stores the output in `M`.
