```
gradients_colocate(loss::PyObject, xs::Union{PyObject, Array{PyObject}}, args...;use_locking::Bool = true, kwargs...)
```

スカラー損失関数 `loss` に対する `xs` の勾配を計算します。勾配はフォワードパスに関してコロケートされています。この関数は通常、分散コンピューティングで使用されます。
