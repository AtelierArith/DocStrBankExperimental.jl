```julia
function confusionMat(yTrue::IntVector, yPred::IntVector)
```

Return the *confusion matrix* expressing *frequencies* (counts), given integer vectors of true label `yTrue` and predicted labels `yPred`.

The length of `yTrue` and `yPred` must be equal. Furthermore, the `yTrue` vector must comprise all natural numbers in between 1 and *z*, where *z* is the number of classes.

The confusion matrix will have size *z*. It is computed starting from a matrix filled everywhere with zeros and adding, for each label, 1 at entry [`i`, `j`] of the matrix, where `i` is the true label and `j` the predicted label. Thus, the first row will report the true labels for class 1,  the second row the true labels for class 2, etc.

The returned matrix is a matrix of integers.

**See** [`predict`](@ref), [`predictAcc`](@ref), [`predictErr`](@ref)

**Examples**

```julia
using PosDefManifoldML
confusionMat([1, 1, 1, 2, 2], [1, 1, 1, 1, 2])
# return: [3 0; 1 1]
```
