```
load_system_op(opname::String, grad::Bool=true; multiple::Bool=false)
```

カスタムオペレーターをCustomOpsディレクトリからロードします（TensorFlowの代わりにADCMEに付属）。例えば 

```
s = "SparseOperator"
oplib = "libSO"
grad = true
```

これにより、JuliaはMACOSX上でライブラリ`CustomOps/SparseOperator/libSO.dylib`を見つけるようになります。
