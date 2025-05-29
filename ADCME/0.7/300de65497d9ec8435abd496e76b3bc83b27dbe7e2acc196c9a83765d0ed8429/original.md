```
load_op_and_grad(oplibpath::Union{PyObject, String}, opname::String; multiple::Bool=false)
```

Loads the operator `opname` from library `oplibpath`; gradients are also imported.  If `multiple` is true, the operator is assumed to have multiple outputs. 
