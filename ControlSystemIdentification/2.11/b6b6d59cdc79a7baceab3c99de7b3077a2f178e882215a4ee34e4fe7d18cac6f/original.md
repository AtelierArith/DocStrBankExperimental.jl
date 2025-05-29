```
getARXregressor(y::AbstractVector,u::AbstractVecOrMat, na, nb; inputdelay = ones(Int, size(nb)))
```

Returns a shortened output signal `y` and a regressor matrix `A` such that the least-squares ARX model estimate of order `na,nb` is `y\A`

Return a regressor matrix used to fit an ARX model on, e.g., the form `A(z)y = B(z)u` with output `y` and input `u` where the order of autoregression is `na`, the order of input moving average is `nb` and an optional input delay `inputdelay`. Caution, changing the input delay changes the order to `nb + inputdelay - 1`. An `inputdelay = 0` results in a direct term. 

# Example

```julia
A     = [1,2*0.7*1,1] # A(z) coeffs
B     = [10,5] # B(z) coeffs
u     = randn(100) # Simulate 100 time steps with Gaussian input
y     = filt(B,A,u)
yr,A  = getARXregressor(y,u,3,2) # We assume that we know the system order 3,2
x     = A\yr # Estimate model polynomials
plot([yr A*x], lab=["Signal" "Prediction"])
```

For nonlinear ARX-models, see [BasisFunctionExpansions.jl](https://github.com/baggepinnen/BasisFunctionExpansions.jl/). See also `arx`
