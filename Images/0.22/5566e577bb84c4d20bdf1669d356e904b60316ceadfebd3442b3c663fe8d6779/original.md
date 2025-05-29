```
phase(grad_x, grad_y) -> p
```

Calculate the rotation angle of the gradient given by `grad_x` and `grad_y`. Equivalent to `atan(-grad_y, grad_x)`, except that when both `grad_x` and `grad_y` are effectively zero, the corresponding angle is set to zero.
