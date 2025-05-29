```
linear_map(M::AbstractMatrix, P::VPolygon; [apply_convex_hull]::Bool=false)
```

頂点表現の多角形の具体的な線形写像。

### 入力

  * `M`                 – 行列
  * `P`                 – 頂点表現の多角形
  * `apply_convex_hull` – （オプション; デフォルト: `false`）凸包操作を適用するフラグ（高次元の写像にのみ関連）

### 出力

結果の型は次元によって異なります。1Dでは区間、2Dでは`VPolygon`、それ以外のすべてのケースでは`VPolytope`です。

### アルゴリズム

この実装は内部の`_linear_map_vrep`メソッドを使用します。
