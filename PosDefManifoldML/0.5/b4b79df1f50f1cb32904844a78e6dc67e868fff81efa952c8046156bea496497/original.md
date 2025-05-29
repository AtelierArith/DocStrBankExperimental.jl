```julia
(1)
function predictErr(yTrue::IntVector, yPred::IntVector;
		scoring	:: Symbol = :b,
		digits	:: Int=3)
(2)
function predictErr(CM::Union{Matrix{R}, Matrix{S}};
		scoring	:: Symbol = :b,
		digits	:: Int=3) where {R<:Real, S<:Int}
```

Return the complement of the predicted accuracy, that is, 1.0 minus the result of [`predictAcc`](@ref), given

  * (1) the integer vectors of true labels `yTrue` and of predicted labels `yPred`, or
  * (2) a confusion matrix.

**See** [`predictAcc`](@ref), [`confusionMat`](@ref)
