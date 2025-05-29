```
Sine(in_dims::Int, out_dims::Int; omega::Real)
```

Sinusoidal layer.

## Example

```julia
s = Sine(2, 2; omega=30.0f0) # first layer
s = Sine(2, 2) # hidden layer
```
