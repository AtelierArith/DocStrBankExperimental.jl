```
sampleITE(g, doT)
sampleITE(g, doT; samplesPerPosterior=10)
```

因果GPSLCモデルを用いた個別治療効果の推定

パラメータ:

  * `g::`[`GPSLCObject`](@ref): データとハイパーパラメータを含む
  * `doT`: 要求された介入（例：すべての治療を1.0に設定）
  * `samplesPerPosterior`: `g`の各ポスターサンプルごとに引くITEサンプルの数。

返り値:

`ITEsamples`: `n x m` 行列で、`n` は個人の数、`m` はサンプルの数です。
