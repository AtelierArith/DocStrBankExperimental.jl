```
oblateness(P::Planet) = radius(π/2,P)*angularfrequency(P)^2/gravity(P)
```

Constant of `oblateness` at latitude `π/2` for gravitating `Planet` ellipse.

```Julia
julia> oblateness(Earth) # θ ≡ π/2
0.003449786645650386
```
