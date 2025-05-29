`Conv([domainType=Float64::Type,] dim_in::Tuple, h::AbstractVector)`

`Conv(x::AbstractVector, h::AbstractVector)`

配列 `x::AbstractVector` に掛け算をすると、`x` と `h` の間の畳み込みを返す `LinearOperator` を作成します。`conv` を使用し、したがって FFT アルゴリズムを使用します。
