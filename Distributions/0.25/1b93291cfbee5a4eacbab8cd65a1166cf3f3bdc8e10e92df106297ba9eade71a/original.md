```
Erlang(α,θ)
```

The *Erlang distribution* is a special case of a [`Gamma`](@ref) distribution with integer shape parameter.

```julia
Erlang()       # Erlang distribution with unit shape and unit scale, i.e. Erlang(1, 1)
Erlang(a)      # Erlang distribution with shape parameter a and unit scale, i.e. Erlang(a, 1)
Erlang(a, s)   # Erlang distribution with shape parameter a and scale s
```

External links

  * [Erlang distribution on Wikipedia](http://en.wikipedia.org/wiki/Erlang_distribution)
