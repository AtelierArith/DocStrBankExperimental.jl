```
fft(dist::SemiMetric, X::AbstractDatabase, k; verbose=true)
```

Farthest First Traversalアルゴリズムに基づいて、互いに遠く離れた`k`アイテムを選択します。

次のフィールドを持つ名前付きタプルを返します：

  * `centers`は中心のリスト（$X$へのインデックス）を含みます
  * `nn`は最も近い中心のID（$X$の順序で、1から`length(X)`の間の識別子）
  * `nndists`はデータベース内の各オブジェクトから最も近い中心までの距離（$X$の順序で）
  * `dmax`は中心間の最小距離です

`KCenters.jl`の`enet.jl`に基づいています。
