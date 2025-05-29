```
randomize!(D::DeltaComplex; kwargs...) -> Int
```

`D`のエッジをランダムに反転させて、`D`が十分に一般的になるまで反転を続け、試みた反転の数を返します。

`D`が十分に一般的であるかどうかを判断する基準は、その直径を通じて行います。このメソッドは、特定の回数だけ反転を繰り返します。各反転シーケンスの後に直径が計算されます。これを特定の回数繰り返した後、過去の直径測定の分散が計算されます。

理論的には、分散は時間とともに減少するはずです。しかし、ランダムに反転させているため、真に0に収束することはありません。分散に一定の揺らぎが予想され、これにより分散が時折増加することがあります。最後に測定された分散が過去のいくつかの測定よりも大きくなった時点でアルゴリズムは停止します。

# 引数

  * `num_initial_flips::Integer=1000000` : 測定を開始する前に行う反転の数。
  * `num_flips_per_step::Integer=10000` : 各ステップで直径を計算する前に行う反転の数。
  * `variance_interval_size::Integer=10` : 分散を計算する前に保存する直径の数。
  * `lookback_size::Integer=2` : 停止するかどうかを決定するために現在の分散を比較する過去の回数。

# 例

```julia-repl
julia> D = deltacomplex(30,30);
julia> randomize!(D, num_initial_flips=10000, num_flips_per_step = 1000, variance_interval_size=10, lookback_size = 5)
160000
```
