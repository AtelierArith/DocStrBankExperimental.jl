```
struct Node
```

有限要素モデルにおけるノードを表す型です。

  * `ID`: 識別タグ
  * `x`: $x$-座標
  * `y`: $y$-座標
  * `z`: $z$-座標
  * `u_x`: ノードはグローバル$x$軸に沿った移動に対して拘束されていますか？
  * `u_y`: ノードはグローバル$y$軸に沿った移動に対して拘束されていますか？
  * `u_z`: ノードはグローバル$z$軸に沿った移動に対して拘束されていますか？
  * `θ_x`: ノードはグローバル$x$軸を中心とした回転に対して拘束されていますか？
  * `θ_y`: ノードはグローバル$y$軸を中心とした回転に対して拘束されていますか？
  * `θ_z`: ノードはグローバル$z$軸を中心とした回転に対して拘束されていますか？
  * `state`: 現在の状態
