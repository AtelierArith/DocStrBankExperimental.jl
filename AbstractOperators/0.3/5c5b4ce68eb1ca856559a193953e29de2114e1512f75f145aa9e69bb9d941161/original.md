`MIMOFilt([domainType=Float64::Type,] dim_in::Tuple, B::Vector{AbstractVector}, [A::Vector{AbstractVector},])`

`MIMOFilt(x::AbstractMatrix, b::Vector{AbstractVector}, [a::Vector{AbstractVector},])`

Creates a `LinearOperator` which, when multiplied with a matrix `X`, returns a matrix `Y`. Here a Multiple Input Multiple Output system is evaluated: the columns of `X` and `Y` represent the input signals and output signals respectively. 

$$
\mathbf{y}_i = \sum_{j = 1}^{M} \mathbf{h}_{i,j} * \mathbf{x}_j 
$$

where $\mathbf{y}_i$ and $\mathbf{x}_j$ are the $i$-th and $j$-th columns of the output `Y` and input `X` matrices respectively.

The filters $\mathbf{h}_{i,j}$ can be represented either by providing coefficients `B` and `A` (IIR) or `B` alone (FIR). These coefficients must be given in a `Vector` of `Vector`s. 

For example for a `3` by `2` MIMO system (i.e. `size(X,2) == 3` inputs and `size(Y,2) == 2` outputs) `B` must be:

`B = [b11, b12, b13, b21, b22, b23]`

where `bij` are vector containing the filter coeffients of `h_{i,j}`.

```julia
julia> m,n = 10,3; #time samples, number of inputs

julia> B  = [[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.],[1.;0.;1.], ];
      #B = [   b11   ,     b12   ,    b13   ,   b21    ,   b22,       b23    , ]

julia> A  = [[1.;1.;1.],[2.;2.;2.],[      3.],[      4.],[      5.],[      6.], ];
      #A = [   a11   ,     a12   ,    a13   ,   a21    ,   a22,       a23    , ]

julia> op = MIMOFilt(Float64, (m,n), B, A)
※  ℝ^(10, 3) -> ℝ^(10, 2) 

julia> X = randn(m,n); #input signals

julia> Y = op*X;       #output signals

julia> Y[:,1] ≈ filt(B[1],A[1],X[:,1])+filt(B[2],A[2],X[:,2])+filt(B[3],A[3],X[:,3])
true

julia> Y[:,2] ≈ filt(B[4],A[4],X[:,1])+filt(B[5],A[5],X[:,2])+filt(B[6],A[6],X[:,3])
true

```
