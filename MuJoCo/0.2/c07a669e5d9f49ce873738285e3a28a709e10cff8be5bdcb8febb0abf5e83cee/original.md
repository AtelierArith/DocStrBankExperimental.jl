```
mj_angmomMat(m, d, mat, body)
```

Compute subtree angular momentum matrix.

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should be of shape (3, nv).
  * **`body::Int32`**
