```
leq = LinearEquations{FloatType}(x_names::Vector{String}, x_vec_julia_names::AbstractVector,
                                 x_lengths::Vector{Int}, nx_fixedLength::Int, A_is_constant::Bool;
                                 useRecursiveFactorizationUptoSize = 0)
```

線形方程式系 "A*x=b" を `x::Vector{FloatType}` で定義します。

  * `x` はスカラーまたはベクトル変数のセットから構築され、名前は `x_names[i]` で、長さは `x_length[i]` です（つまり `length(x) = sum(x_lengths)`）。 x*names[1:nx*fixedLength] は固定長の要素であり（コンパイル後に次元は変わりません）、x*names[nx*fixedLength+1:end] はコンパイル後に次元が変わる可能性のあるベクトル値の要素です。
  * `x_vec_julia_names` はベクトル値の要素のJulia名です。
  * `A_is_constant = true` の場合、`A` は初期化後に定数となる行列です。
  * length(x) <= useRecursiveFactorizationUptoSize の場合、線形方程式系はデフォルトの `lu!(..)` および `ldiv!(..)` の代わりに `RecursiveFactorization.jl` を使用して解決されます。

このコンストラクタの使用方法の詳細については、[`LinearEquationsIteration!`](@ref) を参照してください。
