```
range = outputrange(P::AbstractProcess)
```

プロセスの出力（測定信号）の範囲を返します。`range`はタプルのベクトルであり、`length(range) = num_outputs(P)、eltype(range) = Tuple(Real, Real)`です。
