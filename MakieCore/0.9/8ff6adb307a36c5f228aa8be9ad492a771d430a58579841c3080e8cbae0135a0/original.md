```
Plot(args::Vararg{DataType,N})
```

Returns the Plot type that represents the signature of `args`. Example:

```julia
Plot(Vector{Point2f}) == Plot{plot, Tuple{<:Vector{Point2f}}}
```

This can be used to more conveniently create recipes for `plot(mytype)` without the recipe macro:

```julia
struct MyType ... end

function Makie.plot!(plot::Plot(MyType))
    ...
end

plot(MyType(...))
```
