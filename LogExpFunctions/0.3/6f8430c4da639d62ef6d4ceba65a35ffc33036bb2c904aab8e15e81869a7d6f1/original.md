```julia
log1pexp(x)

```

Return `log(1+exp(x))` evaluated carefully for largish `x`.

This is also called the ["softplus"](https://en.wikipedia.org/wiki/Rectifier_(neural_networks)) transformation, being a smooth approximation to `max(0,x)`. Its inverse is [`logexpm1`](@ref).

This is also called the ["softplus"](https://en.wikipedia.org/wiki/Rectifier_(neural_networks)) transformation (in its default parametrization, see [`softplus`](@ref)), being a smooth approximation to `max(0,x)`. 

See:

  * Martin Maechler (2012) [“Accurately Computing log(1 − exp(− |a|))”](http://cran.r-project.org/web/packages/Rmpfr/vignettes/log1mexp-note.pdf)
