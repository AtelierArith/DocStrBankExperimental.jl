```
 BlockPreconditioner(;partitioning, factorization=LUFactorization)
```

`partitioning`によって与えられた未知数の分割からブロック前処理器を作成します。`partitioning`は行列のパーティションのインデックスを記述するAbstractVectorsのベクターです。サイズが`n x n`の行列の場合、例えば`partitioning`は`[ 1:n÷2, (n÷2+1):n]`または`[ 1:2:n, 2:2:n]`のようになります。`factorization`は、Aの部分行列から因子分解を作成することを可能にする呼び出し可能な（Functionまたは構造体）ものです（`ldiv!`メソッドを使用）。
