```
surface(x,y,z)
surface!(x,y,z)
```

Draw a 3D surface plot.

# Example

```julia-repl
julia> using LinearAlgebra
julia> x = y = range(-3, stop = 3, length = 100)
julia> surface(x, y, (x, y) -> sinc(norm([x, y])))
```
