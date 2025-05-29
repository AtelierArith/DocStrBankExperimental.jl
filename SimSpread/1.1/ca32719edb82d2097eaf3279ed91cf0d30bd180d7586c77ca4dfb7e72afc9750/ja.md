```
construct(y::NamedMatrix, X::NamedMatrix)
```

ネットワークベースの推論予測のための特徴-ソース-ターゲットネットワークを構築し、隣接行列を返します。

# 引数

  * `y::NamedMatrix` : ソース-ターゲット二部グラフの隣接行列
  * `X::NamedMatrix` : ソース-特徴二部グラフの隣接行列
