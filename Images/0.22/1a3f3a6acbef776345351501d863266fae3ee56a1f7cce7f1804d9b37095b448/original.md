```
m = magnitude(grad_x, grad_y)
```

Calculates the magnitude of the gradient images given by `grad_x` and `grad_y`. Equivalent to `sqrt(grad_x.^2 + grad_y.^2)`.

Returns a magnitude image the same size as `grad_x` and `grad_y`.
