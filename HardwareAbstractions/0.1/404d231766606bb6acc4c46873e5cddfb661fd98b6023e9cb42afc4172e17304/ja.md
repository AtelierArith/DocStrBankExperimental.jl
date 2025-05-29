```
range = inputrange(P::AbstractProcess)
```

プロセスの入力（制御信号）の範囲を返します。`range`はタプルのベクトルであり、`length(range) = num_inputs(P)、eltype(range) = Tuple(Real, Real)`です。
