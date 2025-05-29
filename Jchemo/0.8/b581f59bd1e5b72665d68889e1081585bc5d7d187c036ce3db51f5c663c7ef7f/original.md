```
transf(object::Fdif, X)
transf!(object::Fdif, X::Matrix, M::Matrix)
```

Compute the preprocessed data from a model.

  * `object` : Model.
  * `X` : X-data to transform.
  * `M` : Pre-allocated output matrix (n, p - npoint + 1).

The in-place function stores the output in `M`.
