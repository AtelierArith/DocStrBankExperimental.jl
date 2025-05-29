```
T_dimension(G, R, S)
T_dimension(G::Tuple, R::Tuple, S::Tuple)
T_dimension(G::Int, R::Int, S::Int)
```

GRSモデルの遷移行列の次元を計算します。

# 説明

この関数は、提供されたパラメータに基づいてGRSモデルの遷移行列の次元を計算します。

# 引数

  * `G`: 遺伝子の総数または遺伝子の総数のタプル。
  * `R`: レポータの数またはレポータの数のタプル。
  * `S`: 状態の数または状態の数のタプル。

# メソッド

  * `T_dimension(G, R, S)`: 与えられた整数 `G`、`R`、および `S` の次元を計算します。
  * `T_dimension(G::Tuple, R::Tuple, S::Tuple)`: 与えられたタプル `G`、`R`、および `S` の次元を計算します。
  * `T_dimension(G::Int, R::Int, S::Int)`: 与えられた整数 `G`、`R`、および `S` の次元を計算します。

# 戻り値

  * `Int`: 遷移行列の次元。

```
