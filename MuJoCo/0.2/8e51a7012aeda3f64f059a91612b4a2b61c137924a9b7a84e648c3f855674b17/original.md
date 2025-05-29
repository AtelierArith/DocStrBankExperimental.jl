```
mju_symmetrize(res, mat)
```

Symmetrize square matrix res = (mat + mat')/2.

# Arguments

  * **`res::Matrix{Float64}`** -> A matrix of variable size. `res` and mat should have the same shape.
  * **`mat::Matrix{Float64}`** -> A matrix of variable size. `mat` should be square. res and `mat` should have the same shape. Constant.
