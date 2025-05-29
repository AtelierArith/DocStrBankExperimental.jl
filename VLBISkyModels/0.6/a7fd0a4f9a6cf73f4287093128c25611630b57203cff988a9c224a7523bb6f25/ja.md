```
modify(m::AbstractModel, transforms...)
```

与えられた `model` を `transforms` のセットを使用して修正します。これは、モデル変換のシーケンスを適用することを可能にする最も一般的な関数です。例えば、

```julia-repl
modify(Gaussian(), Stretch(2.0, 1.0), Rotate(π/4), Shift(1.0, 2.0), Renorm(2.0))
```

は、位置角 `π/4` の非対称ガウスを作成し、位置 (1.0, 2.0) にシフトし、フラックスを 2 Jy にします。これは Flux のチェーンに似ています。
