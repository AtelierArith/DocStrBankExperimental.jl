```
smooth!(y, x, λ, f, ∇f!, y_prev)
```

一般的な滑らかな関数 `f` の近接演算子を、インプレース勾配 `∇f!` とスケーリングパラメータ `λ` を用いて `x` で計算し、結果を `y` に格納します。`smooth!` も参照してください。前の解である `y_prev` を使用することで、ウォームスタートが可能です。
