```
observation_matrix(p::SparseTabularPOMDP, a::Int64)
```

スパースタブラーPOMDPの観測モデルのアクセサ関数です。アクションaを取ったときの観測確率を含むスパース行列を返します: O[sp, o] = Pr(o | sp, a)。
