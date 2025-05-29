```
plotsp(X, wl = 1:nco(X); size = (500, 300), color = nothing, nsamp = nothing, 
    kwargs...)
```

Plotting spectra.

  * `X` : X-data (n, p).
  * `wl` : Column names of `X`. Must be numeric.

Keyword arguments:

  * `size` : Size (horizontal, vertical) of the figure.
  * `color` : Set a unique color (and eventually transparency)    to the spectra.
  * `nsamp` : Nb. spectra (X-rows) to plot. If `nothing`,    all spectra are plotted.
  * `kwargs` : Optional arguments to pass in `Axis` of CairoMakie.

The function plots the rows of `X`.

To use `plotxy`, a backend (e.g. CairoMakie) has  to be specified.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
wlst = names(X)
wl = parse.(Float64, wlst) 

plotsp(X).f
plotsp(X; color = (:red, .2)).f
plotsp(X, wl; xlabel = "Wavelength (nm)", ylabel = "Absorbance").f

tck = collect(wl[1]:200:wl[end]) ;
plotsp(X, wl; xlabel = "Wavelength (nm)", ylabel = "Absorbance", xticks = tck).f

f, ax = plotsp(X, wl; color = (:red, .2))
xmeans = colmean(X)
lines!(ax, wl, xmeans; color = :black, linewidth = 2)
vlines!(ax, 1200)
f
```
