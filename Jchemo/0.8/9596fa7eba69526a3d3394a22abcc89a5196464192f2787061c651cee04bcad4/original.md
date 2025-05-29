```
mavg(; kwargs...)
mavg(X; kwargs...)
```

Smoothing by moving averages of each row of X-data.

  * `X` : X-data (n, p).

Keyword arguments:

  * `npoint` : Nb. points involved in the window.

The function returns a matrix (n, p).

The smoothing is computed by convolution with padding,  using function `imfilter` of package ImageFiltering.jl.  The centered kernel is `ones(npoint) / npoint`.  Each returned point is located on the center of the kernel. Assume a signal x of length p (row of `X`) correponding to  a vector wl of p wavelengths (or other indexes). 

If `npoint = 3`, the  kernel is kern = [.33, .33, .33], and: 

  * The output value at index i = 4 is: dot(kern, [x[3], x[4], x[5]]).   The output wavelength is: wl[4]
  * The output value at index i = 1 is: dot(kern, [x[1], x[1], x[2]])    (padding). The corresponding wavelength is: wl[1].

If `npoint = 4`, the  kernel is kern = [.25, .25, .25, .25], and: 

  * The output value at index i = 4 is: dot(kern, [x[3], x[4], x[5], x[6]]).   The corresponding wavelength is: (wl[4] + wl[5]) / 2.
  * The output value at index i = 1 is: dot(kern, x[1], x[1], x[2], x[3])    (padding). The corresponding wavelength is: (wl[1] + wl[2]) / 2.

## References

Package ImageFiltering.jl https://github.com/JuliaImages/ImageFiltering.jl

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

model = mavg(npoint = 10) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
