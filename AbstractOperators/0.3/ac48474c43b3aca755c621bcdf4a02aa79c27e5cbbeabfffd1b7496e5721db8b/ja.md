`MyLinOp(domainType::Type, dim_in::Tuple, [domainType::Type,] dim_out::Tuple, Fwd!::Function, Adj!::Function)`

ユーザー定義の `LinearOperator` を、線形マッピング `Fwd!` とその随伴 `Adj!` を指定して構築します。関数 `Fwd!` と `Adj` は、与えられた次元 `dim_in` と `dim_out`、およびドメインとコドメインの型に一致するインプレース関数でなければなりません。

```julia
julia> n,m = 5,4;

julia> A = randn(n,m);

julia> op = MyLinOp(Float64, (m,),(n,), (y,x) -> mul!(y,A,x), (y,x) -> mul!(y,A',x))
A  ℝ^4 -> ℝ^5

julia> op = MyLinOp(Float64, (m,), Float64, (n,), (y,x) -> mul!(y,A,x), (y,x) -> mul!(y,A',x))
A  ℝ^4 -> ℝ^5

```
