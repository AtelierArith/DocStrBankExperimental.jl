```
SlashedDisk{T}(slash::T) where {T}
```

Tophat disk geometrical model, i.e. the intensity profile

$$
    I(x,y) = \begin{cases} \pi^{-1} & x^2+y^2 < 1 \\ 0 & x^2+y^2 \geq 0 \end{cases}
$$

i.e. a unit radius and unit flux disk.

By default if T isn't given, `Disk` defaults to `Float64`
