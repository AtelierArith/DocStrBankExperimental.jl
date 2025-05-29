```
klu!(K::KLUFactorization, A::SparseMatrixCSC; check=true, allowsingular=false) -> K::KLUFactorization
klu(K::KLUFactorization, nzval::Vector{Tv}; check=true, allowsingular=false) -> K::KLUFactorization
```

KLU因子分解`K`を`A`または`nzval`の値を使用して再計算します。`K`を作成するために使用された元の行列のパターンは、`A`のパターンと一致する必要があります。

実数または複素数要素型の疎行列`A`の場合、`K`の戻り値の型は`KLUFactorization{Tv, Ti}`であり、`Tv`は`Float64`または`ComplexF64`であり、`Ti`は整数型（`Int32`または`Int64`）です。

参照: [`klu`](@ref)

# 引数

  * `K::KLUFactorization`: 以前に`klu`を呼び出して作成された行列因子化オブジェクトで、再因子化されるもの。
  * `A::SparseMatrixCSC`または`n::Integer`, `colptr::Vector{Ti}`, `rowval::Vector{Ti}`, `nzval::Vector{Tv}`: 因子化される疎行列またはゼロベースの疎行列コンポーネント。
  * `check::Bool`: `true`（デフォルト）で因子分解後にエラーをチェックします。`false`の場合、エラーはユーザーが`klu.common.status`でチェックする必要があります。
  * `allowsingular::Bool`: `true`（デフォルトは`false`）の場合、行列が特異であっても因子分解を進めることを許可します。特異性がユーザーによって`klu.common.status == KLU.KLU_SINGULAR`でチェックされない場合、これは

その後の`solve!`または`ldiv!`呼び出しでのゼロ除算エラーを静かに許可します。

!!! note
    `klu(A::SparseMatrixCSC)`は、SuiteSparseの一部であるKLU[^ACM907]ライブラリを使用します。このライブラリは、[`Float64`](@ref)または`ComplexF64`要素を持つ疎行列のみをサポートしているため、`lu`は`A`を`SparseMatrixCSC{Float64}`または`SparseMatrixCSC{ComplexF64}`型のコピーに変換します。


[^ACM907]: Davis, Timothy A., & Palamadai Natarajan, E. (2010). Algorithm 907: KLU, A Direct Sparse Solver for Circuit Simulation Problems. ACM Trans. Math. Softw., 37(3). doi:10.1145/1824801.1824814
