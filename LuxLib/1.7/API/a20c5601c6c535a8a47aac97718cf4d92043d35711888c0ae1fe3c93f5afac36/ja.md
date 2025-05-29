```
batched_matmul(x, y)
```

`x` と `y` のバッチ行列乗算を計算します。詳細については、`NNlib.batched_mul` に関する NNlib ドキュメントを参照してください。この関数は主に `batched_mul` のラッパーですが、CPU 上でより高速になるように試みています。

!!! tip "より高速なバッチ行列乗算を得るには `LoopVectorization.jl` をロードしてください"
    CPU 上で LoopVectorization をロードすると、バッチ行列乗算のより高速な実装が追加されます。

