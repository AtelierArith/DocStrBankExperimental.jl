```
neighborsimplices(A::AbstractMatrix; k, r, dim, symmetric, normalizedist, groupby)
```

最近傍サンプルを接続する単体グラフを作成します。

# 入力

  * `A`: データ行列 (変数 × サンプル)。
  * `k`: 接続する最近傍の数。デフォルト: `0`。
  * `r`: 距離 `≤r` で全ての隣接点を接続。デフォルト: `0.0`。
  * `dim`: 距離を計算する前に次元を `dim` に削減。ノイズを減らすのに便利。デフォルト: 無効。
  * `symmetric`: 単体グラフを対称にする。デフォルト: `false`。
  * `normalizedist`: 距離をスケール [0.0,1.0] に正規化し、点から原点までの最大距離を 0.5 にする。`r` パラメータに影響します。デフォルト: `true`。
  * `groupby`: 指定されたグループ内のサンプルのみを接続。デフォルト: 無効。

# 例

```
julia> sg = neighborsimplices([0 0 2 2; 0 1 1 0]; k=1); sg.G
4×4 BitArray{2}:
 1  1  0  0
 1  1  0  0
 0  0  1  1
 0  0  1  1

julia> sg = neighborsimplices([0 0 2 2; 0 1 1 0]; r=0.45); sg.G
4×4 BitArray{2}:
 1  1  0  1
 1  1  1  0
 0  1  1  1
 1  0  1  1
```
