```
orientation(grad_x, grad_y) -> orient
```

Calculate the orientation angle of the strongest edge from gradient images given by `grad_x` and `grad_y`.  Equivalent to `atan(grad_x, grad_y)`.  When both `grad_x` and `grad_y` are effectively zero, the corresponding angle is set to zero.
