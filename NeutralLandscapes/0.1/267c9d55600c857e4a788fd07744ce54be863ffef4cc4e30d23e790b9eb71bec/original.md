```
rand!(mat, alg) where {IT <: Integer}
```

Fill the matrix `mat` with a landscape created following the model defined by `alg`. The `mask` argument accepts a matrix of boolean values, and is passed to `mask!` if it is not `nothing`. 
