```julia
function binaryloss(yTrue::IntVector, yPred::IntVector)
```

Binary error loss given a vector of true labels `yTrue` and a vector of predicted labels `yPred`. These two vectors must have the same size. The error loss is 1 if the corresponding labels are different, zero otherwise. Return a BitVector, that is, a vector of booleans.

**See** [`predict`](@ref).

**Examples**

```julia
using PosDefManifoldML, Random
dummy1, dummy2, yTr, yPr=gen2ClassData(2, 10, 10, 10, 10, 0.1);
shuffle!(yPr)
[yTr yPr binaryloss(yTr, yPr)]
```
