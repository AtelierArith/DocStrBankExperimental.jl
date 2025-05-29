```
getARXregressor(y::AbstractVector,u::AbstractVecOrMat, na, nb)
```

Returns a shortened output signal `y` and a regressor matrix `A` such that the least-squares ARX model estimate of order `na,nb` is `y\A`

Return a regressor matrix used to fit an ARX model on, e.g., the form `A(z)y = B(z)f(u)` with output `y` and input `u` where the order of autoregression is `na` and the order of input moving average is `nb`

# Example

Here we test the model with the Function `f(u) = √(|u|)`

```julia
A     = [1,2*0.7*1,1] # A(z) coeffs
B     = [10,5] # B(z) coeffs
u     = randn(100) # Simulate 100 time steps with Gaussian input
y     = filt(B,A,sqrt.(abs.(u)))
yr,A  = getARXregressor(y,u,2,2) # We assume that we know the system order 2,2
bfe   = MultiUniformRBFE(A,[1,1,4,4,4], normalize=true)
bfa   = BasisFunctionApproximation(yr,A,bfe, 1e-3)
e_bfe = √(mean((yr - bfa(A)).^2))
plot([yr bfa(A)], lab=["Signal" "Prediction"])
```

See README (`?BasisFunctionExpansions`) for more details
