```
Options(;sparsity=DensePattern(), derivatives=ForwardFD(), solver=IPOPT())
```

SNOWのオプション。デフォルトは密、前方有限差分、および IPOPT です。

# 引数

  * `sparsity::AbstractSparsityPattern`: スパースパターンを指定します
  * `derivatives::AbstractDiffMethod`: 使用する特定の微分方法   または `derivatives::Vector{AbstractDiffMethod}`: 長さ2のベクトル、    最初は勾配微分法、2番目はヤコビアン微分法
  * `solver::AbstractSolver`: 使用する最適化手法を指定します
