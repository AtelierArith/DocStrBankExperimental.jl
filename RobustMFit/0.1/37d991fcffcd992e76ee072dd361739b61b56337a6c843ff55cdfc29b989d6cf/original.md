```
Dagum(a::Real, b::Real, p::Real)
```

The Dagum distribution with parameters `a`, `b` and `p`, see [Wikipedia](https://en.wikipedia.org/wiki/Dagum_distribution)

# Example

```julia
d = Dagum(2, 1, 1)
mean(d)
pdf(d, 1)
```
