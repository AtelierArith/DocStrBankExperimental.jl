```
vm_ngwp(𝚽::Matrix{Float64}, GP_star::GraphPart)
```

varimax NGWP と GP_star.tag をインプレースで構築します。

# 入力引数

  * `𝚽::Matrix{Float64}`: グラフラプラシアンの固有ベクトル 𝚽
  * `GP_star::GraphPart`: 双対グラフの GraphPart オブジェクト

# 出力引数

  * `wavelet_packet::Array{Float64,3}`: varimax NGWP。最初のインデックスは固定レベルでのウェーブレットの選択、2 番目のインデックスはレベル `j` の選択、3 番目のインデックスはウェーブレットベクトル内の要素の選択です。
