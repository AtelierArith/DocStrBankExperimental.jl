```julia
function gen2ClassData(n        ::  Int,
                       k1train  ::  Int,
                       k2train  ::  Int,
                       k1test   ::  Int,
                       k2test   ::  Int,
                       separation :: Real = 0.1)
```

Generate for two classes (1 and 2) a random *training set* holding `k1train`+`k2train` and a random *test set* holding `k1test`+`k2test` symmetric positive definite matrices. All matrices have size *n*x*n*.

The training and test sets can be used to train and test any [MLmodel](@ref).

`separation` is a coefficient determining how well the two classs are separable; the higher it is, the more separable the two classes are. It must be in $[0, 1]$ and typically a value of 0.5 already determines complete separation.

Return a 4-tuple with

  * an [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) holding the `k1train`+`k2train` matrices in the training set,
  * an ℍVector holding the `k1test`+`k2test` matrices in the test set,
  * a vector holding the `k1train`+`k2train` labels (integers) corresponding to the matrices of the training set,
  * a vector holding the `k1test`+`k2test` labels corresponding to the matrices of the test set (*1* for class 1 and *2* for class 2).

**Examples**

```julia
using PosDefManifoldML

PTr, PTe, yTr, yTe=gen2ClassData(10, 30, 40, 60, 80, 0.25)

# PTr=training set: 30 matrices for class 1 and 40 matrices for class 2
# PTe=testing set: 60 matrices for class 1 and 80 matrices for class 2
# all matrices are 10x10
# yTr=a vector of 70 labels for the training set
# yTe=a vector of 140 labels for the testing set

```
