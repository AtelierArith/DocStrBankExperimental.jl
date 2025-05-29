```
differentiate!(jacobian::VecOrMat{Float64}, tsg::TasmanianSG, x::AbstractVector{Float64})
```

returns the derivative (Jacobian or gradient vector) of the interpolant

jacobian:  a vector or a matrix            with dimensions dimensions X outputs            each row corresponds to the value of the interpolant            for one columns of vals tsg:  an instance of TasmanianSG x: a vector with length dimensions which is the evaluation point
