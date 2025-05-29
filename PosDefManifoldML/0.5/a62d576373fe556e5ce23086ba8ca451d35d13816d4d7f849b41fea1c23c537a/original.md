```julia
    function fit!(𝐏 :: ℍVector, pipeline :: Union{Pipeline, Conditioner}; 
        transform = true,
        labels = nothing)
```

Fit the given [`Pipeline`](@ref) (or a single `Conditioner`) to $𝐏$ and return  a fitted `Pipeline` object. $𝐏$ must be of [the ℍVector type](@ref).

A single `Conditioner` can be given as argument instead of a pipeline; a fitted pipeline with a single element will be returned. The type of the conditioner can be gives as well, in which case the default conditioner will be used - see examples below.

If `pipeline` in an empty tuple, return an empty pipeline without doing anything.

if `transform` is true (default), $𝐏$ is transformed (in-place), otherwise the pipeline is fitted but $𝐏$ is not transformed.

If `labels` is a vector of integers holding the class labels of the points  in $𝐏$, the conditioners are supervised (*i.e.*, labels-aware),  otherwise, if it is `nothing` (default), they are unsupervised.  Currently the only conditioners that can behave in a supervised manner is [`Recenter`](@ref). When supervised, the barycenter for recentering is computed given balanced weights to each class, like [`tsWeights`](@ref) does for computing the barycenter used for tangent space mapping. If the classes are balanced, the weighting has no effect.

The returned pipeline can be used as argument for the  [`transform!`](@ref) function, ensuring that the fitted parameters are properly applied. It can also be saved to a file using the [`saveas`](@ref) function and loaded from a file using the [`load`](@ref) function.

Note that the pipeline given as argument is not modified.

**Learning parameters during fit**

For some of the conditioners there is no parameter to be learnt during training.  For those, a call to the `fit!` function is equivalent to a call to the [`transform!`](@ref) function, with the exception that when the `fit!` function is called the parameters used for the tranformation are stored in the returned pipeline.

**See also**: [`transform!`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

## Example 1 (single conditioner): 

# Generate some data
P=randP(3, 5) # 5 random 3x3 Hermitian matrices
Q=copy(P)

# Fit the default recentering conditioner (whitening)
pipeline = fit!(P, Recenter) 

# This is equivalent to
pipeline = fit!(Q, Recenter())

pipeline[1].Z # a learnt parameter (whitening matrix)

## Example 2 (pipeline): 

# Fit a pipeline comprising Tikhonov regularization, 
# recentering, compressing and shrinking according to the Fisher metric.
# The matrices in P will be first regularized, then recentered, 
# then compressed and finally shrunk.

P=randP(3, 5)  
Q=copy(P)

pipeline = fit!(P, 
        @→ Tikhonov(0.0001) → Recenter → Compress → Shrink(Fisher; radius=0.01))

# or 
pipeline = fit!(Q, @→ Recenter Compress Shrink(Fisher; radius=0.01))

# The whitening matrices of the the recentering conditioner,
pipeline[1].Z

# The scaling factors of the compressing conditioner,
pipeline[2].β

# and the step-size of the shrinking conditioner
pipeline[3]

## Example 3 (pipeline with a single conditioner):
P=randP(3, 5)  
pipeline = fit!(P, @→ Recenter)
```
