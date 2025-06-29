```
quadgk(f::BatchIntegrand, a,b,c...; kws...)
```

[`quadgk`](@ref)と同様ですが、インプレースの被積分関数の評価点をバッチ処理して同時に評価します。特に、`quadgk`との違いは2つあります。

1. 関数 `f.f!` は `f!(y, x) = y .= f.(x)` の形である必要があります。つまり、被積分関数 `f(x)` の戻り値を最初の引数 `y` にインプレースで書き込みます。（`f!` の戻り値は無視されます。）被積分関数の定義方法については、[`BatchIntegrand`](@ref)を参照してください。
2. `f.max_batch` は適応的な細分化の方法を変更し、複数のセグメントをまとめてバッチ処理します。`max_batch<=4*order+2` を選択すると、非バッチの `quadgk` の結果が再現されますが、`max_batch=n*(4*order+2)` の場合、最大で `2n` のクロンロッドルールが一緒に評価され、わずかに異なる結果を生じることがあり、相対的な許容誤差を使用する際により多くの被積分関数の評価が必要になることがあります。
