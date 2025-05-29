```
plot(x,y;kwargs...)
plot(y;kwargs...)
```

Return a graph of the path with $x$ and $y$ values given by `x` and `y`

`x` defaults to `0:length(y)-1`. `kwargs` are applied to the `Path2D` object representing the line or to the containing `Plot2D`, as appropriate

```
plot(xs::Vector{<:Vector{<:Real}},
     ys::Vector{<:Vector{<:Real}};
     kwargs...)
```

Multiple line graphs in the same figure

```
plot(x,y,z;kwargs...)
plot(z::Array{<:Real,2};kwargs...)
```

A graph of the surface with $x$, $y$, and $z$ values `x`, `y`, and `z`

`x` defaults to `[i-1 for i=1:size(z,1),j=1:size(z,2)]` and `y` defaults to `[j-1 for i=1:size(z,1),j=1:size(z,2)]`

# Examples

```julia-repl
plot(cumsum(randn(100)))
plot(rand(5,5))
```
