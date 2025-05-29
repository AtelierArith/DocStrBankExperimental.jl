```
LPVSS(x, u, v, nc; normalize=true, λ = 1e-3)
```

Linear Parameter-Varying State-space model. Estimate a state-space model with varying coefficient matrices `x(t+1) = A(v)x(t) + B(v)u(t)`. Internally a `MultiRBFE` or `UniformRBFE` spanning the space of `v` is used, depending on the dimensionality of `v`. `x`, `u` and `v` should have time in first dimension. Centers are found automatically using k-means, see `MultiRBFE`.

# Examples

```jldoctest
using Plots, BasisFunctionExpansions
T          = 1000
x,xm,u,n,m = BasisFunctionExpansions.testdata(T)
nc         = 4
v          = 1:T
model      = LPVSS(x, u, v, nc; normalize=true, λ = 1e-3)
xh         = model(x,u,v)

eRMS       = √(mean((xh[1:end-1,:]-x[2:end,:]).^2))

plot(xh[1:end-1,:], lab="Prediction", c=:red, layout=(2,1))
plot!(x[2:end,:], lab="True", c=:blue); gui()
eRMS <= 0.26

# output

true
```
