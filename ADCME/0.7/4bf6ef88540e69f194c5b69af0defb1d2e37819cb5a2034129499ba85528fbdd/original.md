```
gradient_magnitude(l::PyObject, o::Union{Array, PyObject})
```

Returns the gradient sum 

$$
\sqrt{\sum_{i=1}^n \|\frac{\partial l}{\partial o_i}\|^2}
$$

This function is useful for debugging the training
