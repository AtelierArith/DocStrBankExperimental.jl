```
Spring(; kwargs...)(adj_matrix)
spring(adj_matrix; kwargs...)
```

FruchtermanとReingold（1991年、[doi 10.1002/spe.4380211102](https://doi.org/10.1002/spe.4380211102)）のスプリング/反発モデルを使用します。

  * 引力:  `f_a(d) =  d^2 / k`
  * 反発力:  `f_r(d) = -k^2 / d`

ここで、`d`は2つの頂点間の距離であり、頂点間の最適距離`k`は`C * sqrt( area / num_vertices )`として定義され、`C`は調整可能なパラメータです。

ネットワークの隣接行列表現を受け取り、ノードの座標を返します。

## キーワード引数

  * `dim=2`, `Ptype=Float64`: 次元と出力タイプ`Point{dim,Ptype}`を決定します。
  * `C=2.0`: 結果のレイアウトの密度を調整するための定数
  * `iterations=100`: 最大反復回数
  * `initialtemp=2.0`: 初期「温度」、反復ごとの動きを制御します
  * `initialpos=Point{dim,Ptype}[]`

    初期位置の`Vector`または`Dict`を提供します。すべての位置は[-1,1]の間のランダムな座標を使用して初期化されます。ランダムな位置は、この引数で提供されたキー-バリューペアを使用して上書きされます。
  * `pin=[]`: ノードの位置を固定します（更新されません）。ノードインデックス->値のペアリングの`Vector`または`Dict`として指定できます。値は次のいずれかです。

      * `(12, 4.0)` : 初期位置を上書きして固定
      * `true/false` : この位置を固定
      * `(true, false, false)` : 特定の座標のみを固定
  * `seed=1`: ランダムな初期位置のためのシード。
  * `rng=DEFAULT_RNG[](seed)`

    シードに基づいてrngを作成します。デフォルトは`MersenneTwister`で、`DEFAULT_RNG[]`を上書きすることで指定できます。
