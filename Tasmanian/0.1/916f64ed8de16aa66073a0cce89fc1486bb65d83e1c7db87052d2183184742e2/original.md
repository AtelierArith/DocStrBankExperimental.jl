```
 evaluateBatch!(y::AbstractVecOrMat{Float64}, tsg::TasmanianSG, vals::AbstractVecOrMat{Float64})
```

evaluates the intepolant at the points of interest and set the result in `y`

this should be called after the grid has been created and after values have been loaded

y: a vector or a matrix    with dimensions outputs X size(vals, 2)     each columns corresponds to the value of the interpolant    for one columns of vals

vals: a vector or a matrix       with first dimension equal to dimensions       each column in the array is a single requested point
