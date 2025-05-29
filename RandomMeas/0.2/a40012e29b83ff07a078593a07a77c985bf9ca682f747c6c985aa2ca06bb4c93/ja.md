```
FactorizedShadow(measurement_results::Vector{Int}, local_unitary::Vector{ITensor};
                 G::Vector{Float64} = fill(1.0, length(local_unitary)))
```

生の測定結果とユニタリ変換から `FactorizedShadow` オブジェクトを構築します。

# 引数

  * `measurement_results::Vector{Int}`: 各量子ビット/サイトのバイナリ測定結果のベクトル。
  * `local_unitary::Vector{ITensor}`: 測定中に適用されたローカルユニタリ変換のベクトル。
  * G::Vector{Float64}`（オプション）: 測定誤差補正のための`G` 値のベクトル（デフォルト: すべてのサイトに対して 1.0）。

# 戻り値

`FactorizedShadow` オブジェクト。
