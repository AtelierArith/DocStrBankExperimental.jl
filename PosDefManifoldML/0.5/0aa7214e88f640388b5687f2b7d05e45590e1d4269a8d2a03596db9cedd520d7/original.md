```julia
(1) function testCV(cv1::CVresult, cv2::CVresult; 
               	direction = PermutationTests.Both())

(2) function testCV(𝐞₁::Vector{BitVector}, 𝐞₂::Vector{BitVector}; 
               	direction = PermutationTests.Both())

```

(1) Given two [`CVres`](@ref) stuctures `cv1` and `cv2`, which can be obtaoined  calling the [`crval`](@ref) method, performs Bayles's test (Bayles et *al.*, 2020[🎓](@ref)) on the difference in distribution  of the average binary error losses obtained in cross-validations `cv1` and `cv2`.  This can be used to compare the performance obtained by different machine learning models and/or different pre-processing, processing or pre-conditoning pipelines on the same data. 

!!! warning "Be careful"
    When you compare two models and/or pipelines with cross-validation,  do not use keyword argument `shuffle=true` in [`crval`](@ref), as in this case  the actual data composing the folds would not be identical. Also, is you use the `seed` keyword argument, make sure the same seed is employed for the two cross-validations.


(2) The function also accepts as argument the error losses directly,  denoted `𝐞₁` and `𝐞₂` in method (2) here above.  In this case 𝐞₁ and 𝐞₂ are vectors holding the  vectors of error losses obtained at each fold.  The format is the same used to store the error losses in  a [`CVres`](@ref) stucture.

Denoting $μ_1$ and $μ_2$ the average loss for `cv1` and `cv2` (or `𝐞₁` and `𝐞₂`),  respectively, the `direction` keyword argument determines the test directionality:

  * $H_1: μ_1 > μ_2$ (use `direction=PermutationTests.Right()`)
  * $H_1: μ_1 < μ_2$ (use `direction=PermutationTests.Left()`)
  * $H_1: μ_1 <> μ_2$ (use `direction=PermutationTests.Both()`, the default)

In al cases $H_0: μ_1 = μ_2$.

!!! tip "Test direction in terms of accuracy"
    Note that if the test is significant with `direction=PermutationTests.Right()`, the  error loss of `cv1`(or `𝐞₁`) is statistically superior to the error loss of `cv2`(or `𝐞₂`), which means that the accuracy in `cv1`(or `𝐞₁`) is statistically **inferior** to the accuracy  in `cv2`(or `𝐞₂`).


Return the 3-tuple (*z, p, ase*) holding, the $z$ test-statistic (a standard deviate),  the $p$-value and the asymptotic standard error.

!!! warning "Class Inbalance"
    The error lost reflects the accuracy, not the balance accuracy. If the class are inbalanced, the test will be driven by the majority classes. See also the documentation on [`crval`](@ref).


**Examples**:

```julia
using PosDefManifoldML

## Test the performance of the same model and pipeline on different data:

# Generate two sets of random data with the same distribution
P1, _dummyP, y1, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.01)
P2, _dummyP, y2, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.01)

# Perform a cross-validation on the two sets of data
cv1 = crval(MDM(Fisher), P1, y1; scoring=:a)
cv2 = crval(MDM(Fisher), P2, y2; scoring=:a)

z, p, ase = testCV(cv1, cv2) # two-sided test

# This is equivalent to
z, p, ase = testCV(cv1.losses, cv2.losses)

## Test the performance of, for example, different metrics on the same data:

# Generate two sets of random data with the same distribution
P, _dummyP, y, _dummyy = gen2ClassData(10, 40, 40, 30, 40, 0.15)

cv1 = crval(MDM(logEuclidean), P, y; scoring=:a)
cv2 = crval(MDM(Wasserstein), P, y; scoring=:a)

z, p, ase = testCV(cv1, cv2) # two-sided test

```
