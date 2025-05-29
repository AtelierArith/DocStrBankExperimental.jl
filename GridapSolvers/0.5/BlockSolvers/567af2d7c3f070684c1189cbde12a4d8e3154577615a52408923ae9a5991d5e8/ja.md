```
struct BlockDiagonalSolver{N} <: LinearSolver
```

ブロック対角ソルバーを表すソルバー、すなわち 

```
│ A11   0    0  │   │ x1 │   │ r1 │
│  0   A22   0  │ ⋅ │ x2 │ = │ r2 │
│  0    0   A33 │   │ x3 │   │ r3 │
```

ここで `N` は対角ブロックの数です。

# プロパティ:

  * `blocks::AbstractVector{<:SolverBlock}`: ソルバーブロックの行列で、前処理器の各対角ブロックがどのように取得されるかを示します。
  * `solvers::AbstractVector{<:LinearSolver}`: 各対角ブロックに対して1つのソルバーのベクトルです。
