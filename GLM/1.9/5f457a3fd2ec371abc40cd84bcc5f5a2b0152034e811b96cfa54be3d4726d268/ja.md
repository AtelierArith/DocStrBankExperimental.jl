```
predict(mm::AbstractGLM, newX::AbstractMatrix; offset::FPVector=eltype(newX)[],
        interval::Union{Symbol,Nothing}=nothing, level::Real = 0.95,
        interval_method::Symbol = :transformation)
```

モデル `mm` の予測応答を共変量値 `newX` から返し、オプションで `offset` を指定します。

`interval=:confidence` の場合、指定されたカバレッジ `level` に対する上限と下限も返します。デフォルトでは（`interval_method = :transformation`）、間隔は線形予測子の間隔に逆リンクを適用することによって構築されます。`interval_method = :delta` の場合、間隔はデルタ法によって構築され、すなわち線形予測子の周りで予測応答を線形化します。`:delta` メソッドの間隔は点推定の周りで対称ですが、自然パラメータ制約を尊重しません（例えば、確率の下限が負になる可能性があります）。
