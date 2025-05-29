```
SparsePattern(::ForwardAD, func!, ng, x1, x2, x3)
```

3つの異なる位置で導関数を計算することによってスパースパターンを検出します（順方向ADを使用）。3つの場所すべてでゼロであるエントリは、常にゼロであると見なされます。

# 引数

  * `func!::Function`: f = func!(g, x) の形の関数
  * `ng::Int`: 制約の数
  * `x1,x2,x3::Vector{Float}`:: 3つの入力ベクトル。
