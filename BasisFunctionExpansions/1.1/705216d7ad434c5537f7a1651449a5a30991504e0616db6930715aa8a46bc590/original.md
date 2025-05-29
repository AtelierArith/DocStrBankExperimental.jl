```
LPVSS(x, u, nc; normalize=true, λ = 1e-3)
```

Linear Parameter-Varying State-space model. Estimate a state-space model with varying coefficient matrices `x(t+1) = A(v)x(t) + B(v)u(t)`. Internally a `MultiRBFE` spanning the space of `X × U` is used. `x` and `u` should have time in first dimension. Centers are found automatically using k-means, see `MultiRBFE`.

# Examples

```jldoctest
using Plots, BasisFunctionExpansions
x,xm,u,n,m = BasisFunctionExpansions.testdata(1000)
nc         = 10 # Number of centers
model      = LPVSS(x, u, nc; normalize=true, λ = 1e-3) # Estimate a model
xh         = model(x,u) # Form prediction

eRMS       = √(mean((xh[1:end-1,:]-x[2:end,:]).^2))

plot(xh[1:end-1,:], lab="Prediction", c=:red, layout=2)
plot!(x[2:end,:], lab="True", c=:blue); gui()
eRMS <= 0.37

# output

true
```
