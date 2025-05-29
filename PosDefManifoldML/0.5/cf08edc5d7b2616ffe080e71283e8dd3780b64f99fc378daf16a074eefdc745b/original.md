```julia
function transform!(𝐐 :: Union{ℍVector, ℍ}, pipeline :: Union{Pipeline, Conditioner})

```

Given a fitted [`Pipeline`](@ref) (or a single `Conditioner`), transform all matrices  in $𝐐$ using the parameters learnt during the fitting process. Return $𝐐$.

In a training-test setting, a fitted conditioner or pipeline is given as argument  to this function to make sure that the testing data is transformed according to  the parameters learnt during the fitting of training data. More in general, this function can be used to transform in whatever way the data in $𝐐$.

If `pipeline` in an empty tuple, return $𝐐$ without doing anything.

$𝐐$ can be a single Hermitian matrix or a vector of [the ℍVector type](@ref). It is transformed in-place.

!!! warning "Dimension"
    The dimension of matrix(ces) in $𝐐$ must be the same of the dimension of the matrices  used to fit the conditioner or pipeline.


In contrast to the `fit!` function, only instantiated conditioner can be used. For general use, this is transparent to the user as the [`fit!`](@ref) function always returns pipelines with instantiated conditioners.

**See**: [`fit!`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

## Example 1 (single conditioner)

# Generate some 'training' and 'testing' data
PTr=randP(3, 20) # 20 random 3x3 Hermitian matrices
PTe=randP(3, 5) # 5 random 3x3 Hermitian matrices

# Fit the default recentering conditioner (whitening)
# Matrices in PTr will be transformed (recentered)
R = fit!(PTr, Recenter()) 

# Transform PTe using recentering as above
# using the parameters for recentering learnt
# on PTr during the fitting process. 
transform!(PTe, R)

mean(PTr)-I # Should be close to the zero matrix.
mean(PTe)-I # Should not be close to the zero matrix
# as the recentering parameter is learnt on PTr, not on PTe.

## Example 2 (pipeline)

# Generate some 'training' and 'testing' data
PTr=randP(3, 20) # 20 random 3x3 Hermitian matrices
PTe=randP(3, 5) # 5 random 3x3 Hermitian matrices
QTr=copy(PTr)
QTe=copy(PTe)

p = @→ Tikhonov(0.0002) Recenter(; eVar=0.99) Compress Shrink(Fisher; radius=0.01)
pipeline = fit!(QTr, p)
transform!(QTe, pipeline)

## Example 3 (pipeline with a single conditioner):
P=randP(3, 5)  
# For the Equalize conditioner there is no need to fit some data
transform!(P, @→ Equalize)
# This gives an error as Recenter needs to learn parameters (use fit! instead):
transform!(P, @→ Recenter)
```
