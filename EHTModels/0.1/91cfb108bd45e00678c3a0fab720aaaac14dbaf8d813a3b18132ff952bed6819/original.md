```
$(TYPEDEF)
```

Uniform rectangle geometrical model, i.e. the intensity profile

$$
    I(x,y) = \begin{cases} 1 & |x| < 0.5 and |y| < 0.5 \\ 0 & (otherwise) \end{cases}
$$

i.e. a unit length and unit flux rectangle. By default if T isn't given, `Rectangle` defaults to `Float64`
