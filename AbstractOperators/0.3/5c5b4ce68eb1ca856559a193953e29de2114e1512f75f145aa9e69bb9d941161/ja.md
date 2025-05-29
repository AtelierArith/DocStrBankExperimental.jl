`MIMOFilt([domainType=Float64::Type,] dim_in::Tuple, B::Vector{AbstractVector}, [A::Vector{AbstractVector},])`

`MIMOFilt(x::AbstractMatrix, b::Vector{AbstractVector}, [a::Vector{AbstractVector},])`

行列 `X` と掛け算をすると行列 `Y` を返す `LinearOperator` を作成します。ここでは、複数入力複数出力システムが評価されます：`X` と `Y` の列はそれぞれ入力信号と出力信号を表します。

$$
\mathbf{y}_i = \sum_{j = 1}^{M} \mathbf{h}_{i,j} * \mathbf{x}_j 
$$

ここで、$\mathbf{y}_i$ と $\mathbf{x}_j$ はそれぞれ出力 `Y` と入力 `X` 行列の $i$-番目と $j$-番目の列です。

フィルタ $\mathbf{h}_{i,j}$ は、係数 `B` と `A` (IIR) を提供するか、または `B` のみ (FIR) で表すことができます。これらの係数は `Vector` の `Vector` で与えられなければなりません。

例えば、`3` 行 `2` 列の MIMO システム (すなわち `size(X,2) == 3` 入力と `size(Y,2) == 2` 出力) の場合、`B` は次のようになります：

`B = [b11, b12, b13, b21, b22, b23]`

ここで `bij` はフィルタ係数 `h_{i,j}` を含むベクトルです。

```julia
julia> m,n = 10,3; #時間サンプル、入力の数

julia> B  = [[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.], ];
      #B = [   b11   ,     b12   ,    b13   ,   b21    ,   b22,       b23    , ]

julia> A  = [[1.;1.;1.],[2.;2.;2.],[      3.],[      4.],[      5.],[      6.], ];
      #A = [   a11   ,     a12   ,    a13   ,   a21    ,   a22,       a23    , ]

julia> op = MIMOFilt(Float64, (m,n), B, A)
※  ℝ^(10, 3) -> ℝ^(10, 2) 

julia> X = randn(m,n); #入力信号

julia> Y = op*X;       #出力信号

julia> Y[:,1] ≈ filt(B[1],A[1],X[:,1])+filt(B[2],A[2],X[:,2])+filt(B[3],A[3],X[:,3])
true

julia> Y[:,2] ≈ filt(B[4],A[4],X[:,1])+filt(B[5],A[5],X[:,2])+filt(B[6],A[6],X[:,3])
true

```
