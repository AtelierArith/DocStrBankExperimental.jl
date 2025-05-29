```
train(flux, ivar, labels, mask=nothing, verbose=true, quadratic=true)
```

は次の値を返します: theta, scatters キャノンのトレーニングステップを実行します。すなわち、各ピクセルの係数を計算します。

  * `flux` はトレーニングセット内の各星のスペクトルを含みます。 これは `nstars x npixels` であるべきです（行ベクトルはスペクトルです）
  * `ivar` は `flux` と同じ形状の各ピクセルの逆分散を含みます
  * `labels` は各星のラベルを含みます。 これは `nstars x nlabels` であるべきです。 トレーニングの前に二次ラベル空間に拡張されます。
  * `mask`（オプション）は、各ピクセルでスペクトルに影響を与えることが「許可されている」ラベルを指定するブール値の `nlabels x npix` 行列です。

返されるもの:

  * `theta`: キャノン係数を含む行列。 これは `n_expanded_labels x npix` になります
  * `scatters`: 各ピクセルでのモデルの散乱
