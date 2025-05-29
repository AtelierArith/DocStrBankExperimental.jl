```
sampleSATE(g, doT)
sampleSATE(g, doT; samplesPerPosterior=10)
```

因果GPSLCモデルを用いてサンプル平均処置効果を推定します

[`sampleITE`](@ref)を使用して、サンプル平均処置効果のためのサンプルを引き出すことができます

パラメータ:

  * `g::`[`GPSLCObject`](@ref): データとハイパーパラメータを含む
  * `doT`: 要求される介入（例: すべての処置を1.0に設定）
  * `samplesPerPosterior`: `g`の事後サンプルごとに引き出すサンプルの数。

返り値:

`SATEsamples`: `n x m` 行列で、`n` は個体の数、`m` はサンプルの数です。
