```
BS = bs_level(GP::GraphPart, j::Int, c2f::Bool = true)
```

与えられたグラフパーティショニングに対するレベル j に対応する基底を指定します

### 入力引数

  * `GP::GraphPart`: 入力 GraphPart オブジェクト
  * `j::Int`: 基底が対応するレベル (`j = 0` はグローバルレベル)
  * `c2f::Bool`: c2f または f2c のフラグ (デフォルト: true、すなわち c2f)

### 出力引数

  * `BS::BasisSpec`: レベル `j` の基底に対応する BasisSpec オブジェクト
