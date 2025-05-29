```
SFDP(; kwargs...)(adj_matrix)
sfdp(adj_matrix; kwargs...)
```

Hu (2005, The Mathematica Journal, [pdf](http://yifanhu.net/PUB/graph_draw_small.pdf)) によって提案されたスプリング-エレクトリックモデルを使用しています。

力は次のように計算されます：

```
    f_attr(i,j) = ‖xi - xj‖ ² / K ,    i<->j
    f_repln(i,j) = -CK² / ‖xi - xj‖ ,  i!=j
```

ネットワークの隣接行列表現を取り、ノードの座標を返します。

## キーワード引数

  * `dim=2`, `Ptype=Float64`: 次元と出力タイプ `Point{dim,Ptype}` を決定します。
  * `tol=1.0`: 最後のステップの位置変化 `Δp <= tol*K` がすべてのノードで発生した場合に停止します。
  * `C=0.2`, `K=1.0`: 力を調整するためのパラメータ。
  * `iterations=100`: 最大反復回数
  * `initialpos=Point{dim,Ptype}[]`

    初期位置の `Vector` または `Dict` を提供します。すべての位置は [-1,1] の間のランダムな座標を使用して初期化されます。この引数で提供されたキー-バリューペアを使用してランダムな位置が上書きされます。
  * `pin=[]`: ノードの位置を固定します（更新されません）。ノードインデックス -> 値のペアリングの `Vector` または `Dict` として与えることができます。値は次のいずれかです。

      * `(12, 4.0)` : 初期位置を上書きし、固定します
      * `true/false` : この位置を固定します
      * `(true, false, false)` : 特定の座標のみを固定します
  * `seed=1`: ランダムな初期位置のためのシード。
  * `rng=DEFAULT_RNG[](seed)`

    シードに基づいて rng を作成します。デフォルトは `MersenneTwister` で、`DEFAULT_RNG[]` を上書きすることで指定できます。
