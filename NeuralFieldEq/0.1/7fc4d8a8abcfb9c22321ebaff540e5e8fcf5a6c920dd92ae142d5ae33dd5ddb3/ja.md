2D確率的解の場合に利用可能なフィールド：

  * `V`: 3次元配列 `(N x (N x tsaved) x np)`、ここでサブマトリックス `N x N` は `tsaved` 時点での `p-th` 軌道に対応します
  * `meanV`: 全ての `np` 軌道にわたる平均解を持つ行列
  * `x`: $x$ 方向の離散化された空間を持つベクトル
  * `y`: $y$ 方向の離散化された空間を持つベクトル
  * `tsaved`: 解が保存された時間の瞬間（補助的目的）
  * `N`: サイズ N x N の行列（補助的目的）。

## 利用可能なメソッド：

領域は `x=x1,...,xN` および `y=y1,...,yN` として離散化されました。

2D SNFEを解く： `Vsto = solveNFE(prob,[tj,tk,tl],ϵ,np)`。

  * `Vsto(tj::Float,p::Int)`: `tj` での `p-th` 軌道を返します（行列）
  * `Vsto(tj::Float)`: `tj` での平均解を返します（行列）
  * `Vsto(xi,yj,tk,p)`: `tk` での点 `(xi,yj)` での `p-th` 軌道を返します
  * `Vsto(xi,yj,tk)`: `tk` での点 `(xi,yj)` での平均解を返します
