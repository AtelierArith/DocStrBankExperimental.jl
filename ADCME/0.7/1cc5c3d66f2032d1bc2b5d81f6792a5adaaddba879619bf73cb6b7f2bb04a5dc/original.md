```
gradients_colocate(loss::PyObject, xs::Union{PyObject, Array{PyObject}}, args...;use_locking::Bool = true, kwargs...)
```

Computes the gradients of a **scalar** loss function `loss` with respect to `xs`. The gradients are colocated with respect to the forward pass.  This function is usually in distributed computing. 
