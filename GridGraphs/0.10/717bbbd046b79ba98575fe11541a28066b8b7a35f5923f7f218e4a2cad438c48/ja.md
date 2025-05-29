```
GridGraph{
    R<:Real,
    W<:AbstractMatrix{R},
    A<:AbstractMatrix{Bool},
    D<:NTuple{<:Any,GridDirection}
}
```

頂点の長方形グリッドによって定義されるグラフ。

# フィールド

  * `vertex_weights::W`: エッジの重みを定義するために使用される頂点重み行列。
  * `vertex_activities::A`: 頂点の活動行列。グリッド上のすべての頂点は存在しますが、アクティブな頂点のみがエッジを持つことができます（非アクティブな頂点は孤立しており、障害物に対応します）。
  * `directions::D`: エッジを定義するために使用される合法的な方向のセット。
  * `nb_corners_for_diag::Int`: 対角エッジが存在するために必要なアクティブなコーナー頂点の数。値は `0`、`1` または `2` を取ることができます。
  * `pythagoras_cost_for_diag::Bool`: 対角エッジの重みがアクティブなコーナーパスの最短経路を使用して計算されるか（`true`）、単に到着頂点の重みを使用するか（`false`）を示します。

# コンストラクタ

以下のデフォルト値を持つユーザーフレンドリーなコンストラクタがあります：

```
GridGraph(
    vertex_weights;
    vertex_activities=Trues(size(weights)),
    directions=ROOK_DIRECTIONS,
    nb_corners_for_diag=0,
    pythagoras_cost_for_diag=false
)
```
