```
scaled_gauss_aux(μ, meas, storage=similar(μ); read_var=0)
```

`μ`と`meas`のスケーリングされたガウス損失を計算します。`read_var=0`はセンサーの読み出しノイズ分散です。`μ`は`meas`よりも大きなサイズである可能性があります。その場合、`meas`と同じサイズの`μ`から中心領域を抽出します。
