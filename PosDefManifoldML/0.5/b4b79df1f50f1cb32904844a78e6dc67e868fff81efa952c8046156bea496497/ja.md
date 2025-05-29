```julia
(1)
function predictErr(yTrue::IntVector, yPred::IntVector;
		scoring	:: Symbol = :b,
		digits	:: Int=3)
(2)
function predictErr(CM::Union{Matrix{R}, Matrix{S}};
		scoring	:: Symbol = :b,
		digits	:: Int=3) where {R<:Real, S<:Int}

予測された精度の補完、すなわち、1.0 から [`predictAcc`](@ref) の結果を引いた値を返します。与えられた条件は以下の通りです。

  * (1) 真のラベルの整数ベクトル `yTrue` と予測されたラベルの整数ベクトル `yPred`、または
  * (2) 混同行列。

**参照** [`predictAcc`](@ref)、[`confusionMat`](@ref)
```
