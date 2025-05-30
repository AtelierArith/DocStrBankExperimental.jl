```
ignore_derivatives(x)
```

Tells the AD system to ignore the gradients of the argument. Can be used to avoid unnecessary computation of gradients.

```julia
ignore_derivatives(x) * w
```
