```
wdis(d; typw = :bisquare, alpha = 0)
```

Different functions to compute weights from distances.

  * `d` : Vector of distances.

Keyword arguments:

  * `typw` : Define the weight function.
  * `alpha` : Parameter of the weight function,    see below.

The returned weight vector is: 

  * w = f(`d` / q) where f is the weight function    and q the 1-`alpha` quantile of `d`    (Cleveland & Grosse 1991).

Possible values for `typw` are: 

  * :bisquare: w = (1 - d^2)^2
  * :cauchy: w = 1 / (1 + d^2)
  * :epan: w = 1 - d^2
  * :fair: w =  1 / (1 + d)^2
  * :invexp: w = exp(-d)
  * :invexp2: w = exp(-d / 2)
  * :gauss: w = exp(-d^2)
  * :trian: w = 1 - d
  * :tricube: w = (1 - d^3)^3

## References

Cleveland, W.S., Grosse, E., 1991. Computational methods for local regression.  Stat Comput 1, 47–62. https://doi.org/10.1007/BF01890836

## Examples

```julia
using Jchemo, CairoMakie, Distributions

d = sort(sqrt.(rand(Chi(1), 1000)))
colm = cgrad(:tab10, collect(1:9)) ;
alpha = 0
f = Figure(size = (600, 500))
ax = Axis(f, xlabel = "d", ylabel = "Weight")
typw = :bisquare
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[1])
typw = :cauchy
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[2])
typw = :epan
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[3])
typw = :fair
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[4])
typw = :gauss
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[5])
typw = :trian
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[6])
typw = :invexp
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[7])
typw = :invexp2
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[8])
typw = :tricube
w = wdis(d; typw, alpha)
lines!(ax, d, w, label = String(typw), color = colm[9])
axislegend("Function", position = :lb)
f[1, 1] = ax
f
```
