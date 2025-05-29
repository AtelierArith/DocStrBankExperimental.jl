```
a_star(g, s, t[, distmx][, heuristic][, edgetype_to_return])
```

[A*探索アルゴリズム](http://en.wikipedia.org/wiki/A%2A_search_algorithm)を使用して最短経路を計算します。

エッジのベクトルを返します。

# 引数

  * `g::AbstractGraph`: グラフ
  * `s::Integer`: 始点
  * `t::Integer`: 終点
  * `distmx::AbstractMatrix`: オプションの（おそらく疎な）`n × n`エッジ重みの行列。デフォルトでは`weights(g)`に設定されています（これは[`Graphs.DefaultDistance`](@ref)にフォールバックします）。
  * `heuristic`: 各頂点を`v`から`t`までの残りの距離の下限推定にマッピングするオプションの関数。デフォルトでは`v -> 0`に設定されています（これはダイクストラのアルゴリズムに対応します）。ヒューリスティック値はエッジ重みと同じ型である必要があります！
  * `edgetype_to_return::Type{E}`: 戻り値ベクトル内のエッジの型`E<:AbstractEdge`。デフォルトでは`edgetype(g)`に設定されています。重み付きエッジの場合でも、二引数コンストラクタ`E(u, v)`が定義されている必要があります：定義されていない場合は、`E = Graphs.SimpleEdge`の使用を検討してください。

!!! warning
    経路を構築するために二引数エッジコンストラクタ`E(u, v)`が使用されるため、エッジに関連付けられたメタデータ（その重みなど）は結果に失われます。後処理ステップを自分でコーディングする必要があるかもしれません。

