```
payoff_profile_array(g)
```

N次元のベクトルの配列を返します。各(a*1, ..., a*N)エントリには、アクションプロファイル(a*1, ..., a*N)に対する各プレイヤーのNのペイオフ値のベクトルが含まれます。

# 引数

  * `g::NormalFormGame` : N人プレイヤーの`NormalFormGame`インスタンス。

# 返り値

  * `::Array{Vector,N}` : ペイオフプロファイルの配列。
