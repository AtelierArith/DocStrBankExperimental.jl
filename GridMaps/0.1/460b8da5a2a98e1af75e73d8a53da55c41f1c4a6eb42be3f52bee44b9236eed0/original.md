A variable of GridMap type can itself be called to retrieve map values. This method accepts a single vector (the location), returns a scalar (the value at that point).

# Examples

```julia
data = reshape(1:25, 5, 5)
gmap = GridMap(data)

x = [.2, .75]
val = gmap(x) # returns the value at a single 2D point
val2 = gmap[1,4] # can also use as if it's just the underlying matrix
```
