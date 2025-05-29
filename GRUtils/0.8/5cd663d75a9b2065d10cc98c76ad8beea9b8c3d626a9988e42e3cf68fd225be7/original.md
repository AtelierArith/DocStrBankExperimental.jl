```
stem(x[, y, spec; kwargs...])
stem(x1, y1, x2, y2...; kwargs...)
stem(x1, y1, spec1...; kwargs...)
```

Draw a stem plot

The coordinates and format of the stems and markers are defined as for line plots (cf. [`plot`](@ref)).

Additionally, the keyword argument `baseline` can be used to define the Y coordinate where stems should start from.

# Examples

```julia
# Create example data
x = LinRange(-2, 2, 40)
y = x.^3 .+ x.^2 .+ x .+ 6
# Plot x and y, with dashed stems ended in a star
stem(x, y, "--p")
# Move the baseline to 5
stem(x, y, baseline = 5)

```
