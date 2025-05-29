`MatrixOp(domainType=Float64::Type, dim_in::Tuple, A::AbstractMatrix)`

`MatrixOp(A::AbstractMatrix)`

`MatrixOp(A::AbstractMatrix, n_colons)`

`LinearOperator`を作成します。これは、ベクトル`x::AbstractVector`と掛け算をすると、積`A*x`を返します。

入力`x`は行列でも構いません：列の数は、`dim_in::Tuple`の2番目のエントリで指定するか、コンストラクタ`MatrixOp(A::AbstractMatrix, n_colons)`を使用して指定する必要があります。

```julia
julia> MatrixOp(Float64,(10,),randn(20,10))
▒  ℝ^10 -> ℝ^20 

julia> MatrixOp(randn(20,10))
▒  ℝ^10 -> ℝ^20

julia> MatrixOp(Float64,(10,20),randn(20,10))
▒  ℝ^(10, 20) -> ℝ^(20, 20)

julia> MatrixOp(randn(20,10),4)
▒  ℝ^(10, 4) -> ℝ^(20, 4)

```
