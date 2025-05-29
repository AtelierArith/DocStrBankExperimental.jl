```
speed(θ,P::Planet) = cos(θ)*radius(θ,P)*angularfrequency(P)
```

惑星 `Planet` の緯度 `θ` における恒星回転による速度成分 (m⋅s⁻¹)。

```Julia
julia> speed(0,Earth)
465.1010942547186
```
