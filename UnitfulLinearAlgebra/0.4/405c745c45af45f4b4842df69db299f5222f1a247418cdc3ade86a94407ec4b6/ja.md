```
function dsvd(A::AbstractMultipliableMatrix,Prange::UnitSymmetricMatrix,Pdomain::UnitSymmetricMatrix;full=false,alg::LinearAlgebra.Algorithm = LinearAlgebra.default_svd_alg(A.numbers)) 

次元特異値分解 (DSVD)。
非均一行列に適したSVDのバージョン。
`svd`は`Number`、`Adjoint`、`Transpose`、および`Integers`に対して計算できますが、`dsvd`はまだこれらを実装していません。
```

# 入力

  * `A::AbstractMultipliableMatrix`
  * `Pr::UnitSymmetricMatrix`: 範囲のノルムを定義する正方行列
  * `Pd::UnitSymmetricMatrix`: ドメインのノルムを定義する正方行列
  * `full=false`: オプション引数
  * `alg`: アルゴリズムのオプション引数

# 出力:

  * `F::DSVD`: 分解可能な単位を持つ次元SVDオブジェクト
