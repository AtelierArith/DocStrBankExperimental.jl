```
Linesearch <: Stepsize
```

An abstract functor to represent line search type step size determinations, see [`Stepsize`](@ref) for details. One example is the [`ArmijoLinesearch`](@ref) functor.

Compared to simple step sizes, the line search functors provide an interface of the form `(p,o,i,η) -> s` with an additional (but optional) fourth parameter to provide a search direction; this should default to something reasonable, most prominently the negative gradient.
