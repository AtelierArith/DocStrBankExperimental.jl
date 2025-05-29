```
WithGraph(model, g::GNNGraph; traingraph=false)
```

A type wrapping the `model` and tying it to the graph `g`. In the forward pass, can only take feature arrays as inputs, returning `model(g, x...; kws...)`.

If `traingraph=false`, the graph's parameters won't be part of  the `trainable` parameters in the gradient updates.

# Examples

```julia
g = GNNGraph([1,2,3], [2,3,1])
x = rand(Float32, 2, 3)
model = SAGEConv(2 => 3)
wg = WithGraph(model, g)
# No need to feed the graph to `wg`
@assert wg(x) == model(g, x)

g2 = GNNGraph([1,1,2,3], [2,4,1,1])
x2 = rand(Float32, 2, 4)
# WithGraph will ignore the internal graph if fed with a new one. 
@assert wg(g2, x2) == model(g2, x2)
```
