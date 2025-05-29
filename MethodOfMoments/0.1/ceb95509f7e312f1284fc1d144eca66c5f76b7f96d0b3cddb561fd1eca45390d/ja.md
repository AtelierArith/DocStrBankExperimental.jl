```
ClusterVCE(data, clusternames, nparam::Integer, nmoment::Integer; kwargs...)
```

多方向クラスターロバスト分散共分散推定量の仕様とキャッシュのためのオブジェクトを構築します。クラスタは`data`から`clusternames`によって特定されます。関連するGMM問題は`nparam`パラメータと`nmoment`モーメント条件を含みます。

# キーワード

  * `Sadj::Union{Real,Nothing}=nothing`: `S`を調整するための係数。
  * `TF::Type=Float64`: 数値の値の型。
