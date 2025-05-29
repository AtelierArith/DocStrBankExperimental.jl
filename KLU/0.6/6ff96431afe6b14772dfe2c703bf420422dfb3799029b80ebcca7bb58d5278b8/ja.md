```
klu(A::SparseMatrixCSC) -> K::KLUFactorization
klu(n, colptr::Vector{Ti}, rowval::Vector{Ti}, nzval::Vector{Tv}) -> K::KLUFactorization
```

スパース行列 `A` の LU 因子分解を KLU[^ACM907] を使用して計算します。

実数または複素数要素型のスパース `A` に対して、`K` の戻り値の型は `KLUFactorization{Tv, Ti}` であり、`Tv` はそれぞれ `Float64` または `ComplexF64` で、`Ti` は整数型（`Int32` または `Int64`）です。

因子分解 `K` の個々のコンポーネントにはインデックスを使用してアクセスできます：

| コンポーネント | 説明                              |
|:------- |:------------------------------- |
| `L`     | 対角ブロックの `LU` の `L`（下三角）部分       |
| `U`     | 対角ブロックの `LU` の `U`（上三角）部分       |
| `F`     | オフ対角ブロックの `LU + F` の `F`（上三角）部分 |
| `p`     | 右置換 `Vector`                    |
| `q`     | 左置換 `Vector`                    |
| `Rs`    | スケーリング係数の `Vector`              |

`K` と `A` の関係は次の通りです：

`K.L * K.U + K.F  == K.Rs` \ `A[K.p, K.q]`

`K` はさらに以下の関数をサポートしています：

  * `LinearAlgebra.\`

# 引数

  * `A::SparseMatrixCSC` または `n::Integer`, `colptr::Vector{Ti}`, `rowval::Vector{Ti}`, `nzval::Vector{Tv}`: 因子分解されるスパース行列またはゼロベースのスパース行列コンポーネント。
  * `check::Bool`: `true`（デフォルト）で因子分解後にエラーをチェックします。`false` の場合、エラーはユーザーが `klu.common.status` でチェックする必要があります。
  * `allowsingular::Bool`: `true`（デフォルト `false`）の場合、行列が特異であっても因子分解を進めることを許可します。特異性がユーザーによって `klu.common.status == KLU.KLU_SINGULAR` でチェックされない場合、以降の `solve!` または `ldiv!` 呼び出しで静かなゼロ除算エラーが発生することがあります。

!!! note
    `klu(A::SparseMatrixCSC)` は SuiteSparse の一部である KLU[^ACM907] ライブラリを使用します。このライブラリは [`Float64`](@ref) または `ComplexF64` 要素を持つスパース行列のみをサポートしているため、`lu` は `A` を適切に `SparseMatrixCSC{Float64}` または `SparseMatrixCSC{ComplexF64}` 型のコピーに変換します。


[^ACM907]: Davis, Timothy A., & Palamadai Natarajan, E. (2010). Algorithm 907: KLU, A Direct Sparse Solver for Circuit Simulation Problems. ACM Trans. Math. Softw., 37(3). doi:10.1145/1824801.1824814
