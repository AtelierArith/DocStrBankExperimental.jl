```
dmatrix_flatten(dmatrix::Array{Float64,3}, flatten::Any)
```

Flatten dmatrix using the method specified by the string "flatten"

### Input Arguments

  * `dmatrix::Array{Float64,3}`: the matrix of expansion coefficients; after this function is called, it becomes the size of (~, ~, 1).
  * `flatten::Any`: the method for flattening dmatrix (see the code in details)
