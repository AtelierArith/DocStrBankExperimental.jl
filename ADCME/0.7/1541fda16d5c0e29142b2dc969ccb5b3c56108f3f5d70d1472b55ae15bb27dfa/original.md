```
load_system_op(opname::String, grad::Bool=true; multiple::Bool=false)
```

Loads custom operator from CustomOps directory (shipped with ADCME instead of TensorFlow) For example 

```
s = "SparseOperator"
oplib = "libSO"
grad = true
```

this will direct Julia to find library `CustomOps/SparseOperator/libSO.dylib` on MACOSX
