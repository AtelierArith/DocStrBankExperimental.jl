```
dmnorm(; kwargs...)
dmnorm(X; kwargs...)
dmnorm!(X::Matrix; kwargs...)
dmnorm(mu, S; kwargs...)
dmnorm!(mu::Vector, S::Matrix; kwargs...)
```

Normal probability density estimation.

  * `X` : X-data (n, p) used to estimate the mean `mu` and    the covariance matrix `S`. If `X` is not given,    `mu` and `S` must be provided in `kwargs`.
  * `mu` : Mean vector of the normal distribution.
  * `S` : Covariance matrix of the Normal distribution.

Keyword arguments:

  * `simpl` : Boolean. If `true`, the constant term and    the determinant in the Normal density formula are set to 1.

Data `X` can be univariate (p = 1) or multivariate (p > 1). See examples.

When `simple` = `true`, the determinant of the covariance matrix  (object `detS`) and the constant (2 * pi)^(-p / 2) (object `cst`)  in the density formula are set to 1. The function returns a pseudo  density that resumes to exp(-d / 2), where d is the squared Mahalanobis  distance to the center `mu`. This can for instance be useful when the number  of columns (p) of `X` becomes too large, with the possible consequences that:

  * `detS` tends to 0 or, conversely, to infinity;
  * `cst` tends to 0,

which makes impossible to compute the true density. 

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "iris.jld2") 
@load db dat
@names dat
X = dat.X[:, 1:4] 
y = dat.X[:, 5]
n = nro(X)
tab(y) 

nlv = 2
model0 = fda(; nlv)
fit!(model0, X, y)
@head T = transf(model0, X)
n, p = size(T)

#### Probability density in the FDA score space (2D)
#### Example of class Setosa 
s = y .== "setosa"
zT = T[s, :]
m = nro(zT)

#### Bivariate distribution
model = dmnorm()
fit!(model, zT)
fitm = model.fitm
@names fitm
fitm.Uinv 
fitm.detS
@head pred = predict(model, zT).pred

## Direct syntax
mu = colmean(zT)
S = covm(zT, mweight(ones(m))) * m / (m - 1) # corrected cov. matrix
fitm = dmnorm(mu, S) ; 
@names fitm
fitm.Uinv
fitm.detS

npoints = 2^7
lims = [(minimum(zT[:, j]), maximum(zT[:, j])) for j = 1:nlv]
x1 = LinRange(lims[1][1], lims[1][2], npoints)
x2 = LinRange(lims[2][1], lims[2][2], npoints)
z = mpar(x1 = x1, x2 = x2)
grid = reduce(hcat, z)
model = dmnorm()
fit!(model, zT)
res = predict(model, grid) ;
pred_grid = vec(res.pred)
f = Figure(size = (600, 400))
ax = Axis(f[1, 1];  title = "Density for FDA scores (Iris - Setosa)", 
    xlabel = "Score 1", ylabel = "Score 2")
co = contour!(ax, grid[:, 1], grid[:, 2], pred_grid; levels = 10, labels = true)
scatter!(ax, T[:, 1], T[:, 2], color = :red, markersize = 5)
scatter!(ax, zT[:, 1], zT[:, 2], color = :blue, markersize = 5)
#xlims!(ax, -12, 12) ;ylims!(ax, -12, 12)
f

#### Univariate distribution
j = 1
x = zT[:, j]
model = dmnorm()
fit!(model, x)
pred = predict(model, x).pred 
f = Figure()
ax = Axis(f[1, 1]; xlabel = string("FDA-score ", j))
hist!(ax, x; bins = 30, normalization = :pdf)  # area = 1
scatter!(ax, x, vec(pred); color = :red)
f

x = zT[:, j]
npoints = 2^8
lims = [minimum(x), maximum(x)]
#delta = 5 ; lims = [minimum(x) - delta, maximum(x) + delta]
grid = LinRange(lims[1], lims[2], npoints)
model = dmnorm()
fit!(model, x)
pred_grid = predict(model, grid).pred 
f = Figure()
ax = Axis(f[1, 1]; xlabel = string("FDA-score ", j))
hist!(ax, x; bins = 30, normalization = :pdf)  # area = 1
lines!(ax, grid, vec(pred_grid); color = :red)
f
```
