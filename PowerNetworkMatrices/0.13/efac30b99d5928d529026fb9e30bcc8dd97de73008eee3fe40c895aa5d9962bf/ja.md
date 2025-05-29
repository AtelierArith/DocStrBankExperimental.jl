```julia
BA_Matrix(sys; reduce_radial_branches)

```

与えられたシステムからBA行列を構築します

# 引数

  * `sys::PSY.System`:       行列が構築されるPSYシステム
  * `reduce_radial_branches::Bool`:       Trueの場合、システムから削除された放射状ブランチを考慮して行列が構築されます
