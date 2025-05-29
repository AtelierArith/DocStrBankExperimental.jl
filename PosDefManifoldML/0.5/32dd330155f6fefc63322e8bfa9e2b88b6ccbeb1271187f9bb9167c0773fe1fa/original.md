```julia
(1)
function predictAcc(yTrue::IntVector, yPred::IntVector;
		scoring	:: Symbol = :b,
		digits	:: Int=3)

(2)
function predictAcc(CM::Union{Matrix{R}, Matrix{S}};
		scoring	:: Symbol = :b,
		digits	:: Int=3) where {R<:Real, S<:Int}
```

Return the prediction accuracy as a proportion, that is, ∈$[0, 1]$, given

  * (1) the integer vectors of true labels `yTrue` and of predicted labels `yPred`, or
  * (2) a confusion matrix.

The confusion matrix may hold integers, in which case it is interpreted as expressing *frequencies* (counts) or may hold real numbers, in which case it is interpreted as expressing *proportions*.

If `scoring`=:b (default) the **balanced accuracy** is computed. Any other value will make the function returning the regular **accuracy**. Balanced accuracy is to be preferred for unbalanced classes. For balanced classes the balanced accuracy reduces to the regular accuracy, therefore there is no point in using regular accuracy if not to avoid a few unnecessary computations when the class are balanced.

The error is rounded to the number of optional keyword argument `digits`, 3 by default.

**Maths**

The regular *accuracy* is given by sum of the diagonal elements of the confusion matrix expressing *proportions*.

For the *balanced accuracy*, the diagonal elements of the confusion matrix are divided by the respective row sums and their mean is taken.

**See** [`predict`](@ref), [`predictErr`](@ref), [`confusionMat`](@ref)

**Examples**

```julia
using PosDefManifoldML
predictAcc([1, 1, 1, 2, 2], [1, 1, 1, 1, 2]; scoring=:a)
# regular accuracy, return: 0.8
predictAcc([1, 1, 1, 2, 2], [1, 1, 1, 1, 2])
# balanced accuracy, return: 0.75
```
