```
oblateness(P::Planet) = radius(π/2,P)*angularfrequency(P)^2/gravity(P)
```

重力を持つ惑星楕円体の緯度 `π/2` における `oblateness` の定数。

```Julia
julia> oblateness(Earth) # θ ≡ π/2
0.003449786645650386
```
