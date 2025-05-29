```
SparsePattern(diffmethod, func!, ng, lx, ux)
```

境界内の3つのランダムに生成された位置で導関数を計算することによってスパースパターンを検出します。3つの場所すべてでゼロであるエントリは、常にゼロであると見なされます。

# 引数

  * `diffmethod::AbstractDiffMethod`: 導関数を計算するためのメソッド
  * `func!::Function`: f = func!(g, x) の形の関数
  * `ng::Int`: 制約の数
  * `lx::Vector{Float}`: x の下限
  * `ux::Vector{Float}`: x の上限
