```
angularfrequency(P::Planet) = 2π/period(P)
```

惑星の恒星回転の `angularfrequency`（ラジアン毎秒）のレート。

```Julia
julia> angularfrequency(Earth) # rad⋅s⁻¹
7.292115146706924e-5
```
