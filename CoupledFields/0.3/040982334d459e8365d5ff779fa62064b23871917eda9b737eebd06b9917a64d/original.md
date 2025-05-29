```
KernelParameters
```

An abstract type. 

All KernelParameters types contain certain parameters which are later passed to internal functions `Kf` and `∇Kf`. 

A KernelParameters type is set using e.g. `PolynomialKP(X::Matrix{Float64})` or `GaussianKP(X::Matrix{Float64})`. 
