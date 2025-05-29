```
abstract type BinningAlgorithm{Dim}
```

次元 `Dim` のビニングアルゴリズムのための抽象型です。

### 実装

各サブタイプは以下のフィールドを持つべきです：

  * `boundary::Boundary{Dim, CRS}``
  * `bins::Bins{Dim, CRS}`
  * `idx2pos::Vector{Union{Int64, Nothing}}`

各サブタイプは以下を実装するべきです：

  * `membership(data::Matrix, binner)` という関数は、`Dim x N_points` の点の行列を受け取り、ベクトル `memb` を返します。ここで `memb[i] = j` は `data[:,i]` が `binner.bins[j]` の内部にある場合を示し、`memb[i] = nothing` は `data[:,i]` がどのビンにも含まれない場合を示します。
  * `membership(traj::Trajectories, binner)` という関数は `(memb_x0, memb_xT)` を返します。多くの場合、これは `(membership(traj.x0, binner), membership(traj.xT, binner))` によって与えられます。

### メソッド

```
points(binner)
```

各ビンの生の頂点のベクトルを返します。
