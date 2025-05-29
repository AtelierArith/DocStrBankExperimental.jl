```
ShallowShadow(measurement_results::Vector{Int}, local_unitary::Vector{ITensor};
                 G::Vector{Float64} = fill(1.0, length(local_unitary)))
```

生の測定結果とユニタリ変換から `ShallowSShadow` オブジェクトを構築します。

# 引数

  * `measurement_results::Vector{Int}`: 各量子ビット/サイトのバイナリ測定結果のベクトル。
  * `local_unitary::Vector{ITensor}`: 測定中に適用されたローカルユニタリ変換のベクトル。

# 戻り値

`ShallowShadow` オブジェクト。
