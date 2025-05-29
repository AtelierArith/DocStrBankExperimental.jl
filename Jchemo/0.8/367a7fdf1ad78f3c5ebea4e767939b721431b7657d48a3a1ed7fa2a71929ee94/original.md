```
savgol(; kwargs...)
savgol(X; kwargs...)
```

Savitzky-Golay derivation and smoothing of each row of X-data.

  * `X` : X-data (n, p).

Keyword arguments:

  * `npoint` : Size of the filter (nb. points involved in    the kernel). Must be odd and >= 3. The half-window size is    nhwindow = (`npoint` - 1) / 2.
  * `deriv` : Derivation order. Must be: 0 <= `deriv` <= `degree`.
  * `degree` : Degree of the smoothing polynom.   Must be: 1 <= `degree` <= `npoint` - 1.

The smoothing is computed by convolution (with padding), using  function imfilter of package ImageFiltering.jl. Each returned point is  located on the center of the kernel. The kernel is computed with  function `savgk`.

The function returns a matrix (n, p).

## References

Luo, J., Ying, K., Bai, J., 2005. Savitzky–Golay smoothing and differentiation filter for  even number data. Signal Processing 85, 1429–1434. https://doi.org/10.1016/j.sigpro.2005.02.002

Savitzky, A., Golay, M.J.E., 2002. Smoothing and Differentiation of Data by Simplified Least  Squares Procedures. [WWW Document]. https://doi.org/10.1021/ac60214a047

Schafer, R.W., 2011. What Is a Savitzky-Golay Filter? [Lecture Notes].  IEEE Signal Processing Magazine 28, 111–117. https://doi.org/10.1109/MSP.2011.941097

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
year = dat.Y.year
s = year .<= 2012
Xtrain = X[s, :]
Xtest = rmrow(X, s)
wlst = names(dat.X)
wl = parse.(Float64, wlst)
plotsp(X, wl; nsamp = 20).f

npoint = 11 ; deriv = 2 ; degree = 2
model = savgol(; npoint, deriv, degree) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f

####### Gaussian signal 

u = -15:.1:15
n = length(u)
x = exp.(-.5 * u.^2) / sqrt(2 * pi) + .03 * randn(n)
M = 10  # half window
N = 3   # degree
deriv = 0
#deriv = 1
model = savgol(; npoint = 2M + 1, degree = N, deriv)
fit!(model, x')
xp = transf(model, x')
f, ax = plotsp(x', u; color = :blue)
lines!(ax, u, vec(xp); color = :red)
f
```
