```
NeXLMatrixCorrection.estimatecoating(fr::FitResult, substrate::Material, coating::Material, cxr::CharXRay, mc::Type{<:MatrixCorrection}=XPP)::Film
```

バulk `substrate` 上の `coating` の質量厚さを、`fr` に KRatio がある X線 `cxr` を使用して推定します。結果は `fr` のプロパティに割り当てられ、マトリックス補正プロセスで考慮されることができます。

このメソッドは、基板の組成が事前に知られている標準に対して使用することを意図しています。
