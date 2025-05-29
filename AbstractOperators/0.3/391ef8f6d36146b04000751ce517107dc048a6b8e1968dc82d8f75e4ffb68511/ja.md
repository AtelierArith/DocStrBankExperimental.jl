`Filt([domainType=Float64::Type,] dim_in::Tuple, b::AbstractVector, [a::AbstractVector,])`

`Filt(x::AbstractVector, b::AbstractVector, [a::AbstractVector,])`

IIRフィルタの係数`b`と`a`によってフィルタリングされたベクトル`y`を返す`LinearOperator`を作成します。`x::AbstractVector`と掛け算を行うと、`y`が得られます。`b`のみが提供された場合は、代わりにFIRを使用して`y`を計算します。
