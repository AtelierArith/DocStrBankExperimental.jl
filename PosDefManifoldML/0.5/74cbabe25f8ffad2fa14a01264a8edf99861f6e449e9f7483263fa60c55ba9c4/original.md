```julia
function predict(model :: SVMmodel,
			𝐏Te	:: Union{ℍVector, Matrix{Float64}},
			what	:: Symbol = :labels;
		meanISR	:: Union{ℍ, Nothing, UniformScaling} = nothing,
		pipeline:: Union{Pipeline, Nothing} = nothing,
		verbose	:: Bool = true,
		⏩	:: Bool = true)
```

Compute predictions given an [`SVM`](@ref) `model` trained (fitted) on 2 classes and a testing set of *k* positive definite matrices `𝐏Te` of type [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1).

For the meaning of arguments `what`, `meanISR`, `pipeline` and `verbose`, see the documentation of the [`predict`](@ref) function for the ENLR model.

If ⏩ = true (default) and `𝐏Te` is an ℍVector type, the projection onto the tangent space will be multi-threaded. Also, the prediction of the LIBSVM.jl prediction function will be multi-threaded.

**See**: [notation & nomenclature](@ref), [the ℍVector type](@ref)

**See also**: [`fit`](@ref), [`crval`](@ref), [`predictErr`](@ref)

**Examples** 

see the examples for the [`predict`](@ref) function for the ENLR model; the syntax is identical, only the model used there has to be changed with a `SVMmodel`.
