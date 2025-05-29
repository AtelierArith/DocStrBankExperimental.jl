```
Plot(rows::Int64 = 1, cols::Int64 = 1, args...; kwargs...)
```

Makes a figure consists of `rows × cols` subplots. 

# Example

```julia
fig = Plot(3,1)
x = LinRange(0,1,100)
y1 = sin.(x)
y2 = sin.(2*x)
y3 = sin.(3*x)
fig.add_trace(Scatter(x=x, y=y1, name = "Line 1"), row = 1, col = 1)
fig.add_trace(Scatter(x=x, y=y2, name = "Line 2"), row = 2, col = 1)
fig.add_trace(Scatter(x=x, y=y3, name = "Line 3"), row = 3, col = 1)
fig.show()
```
