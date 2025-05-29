```julia
struct CVres <: CVresult
    cvType      :: String
    scoring     :: Union{String, Nothing}
    modelType   :: Union{String, Nothing}
    predLabels  :: Union{Vector{Vector{Vector{I}}}, Nothing} where I<:Int
    losses      :: Union{Vector{BitVector}, Nothing}
    cnfs        :: Union{Vector{Matrix{I}}, Nothing} where I<:Int
    avgCnf      :: Union{Matrix{T}, Nothing} where T<:Real
    accs        :: Union{Vector{T}, Nothing} where T<:Real
    avgAcc      :: Union{Real, Nothing}
    stdAcc      :: Union{Real, Nothing}
    z           :: Union{Real, Nothing}
    p           :: Union{Real, Nothing}
end
```

A call to [`crval`](@ref) results in an instance of this structure.

**Fields:**

`.cvTpe` is the type of cross-validation technique, given as a string (*e.g.*, "10-fold").

`.scoring` is the type of accuracy that is computed, given as a string. This is controlled when calling [`crval`](@ref). Currently *accuracy* and *balanced accuracy* are supported.

`.modelType` is the type of the machine learning model used for performing the cross-validation, given as a string.

`.predLabels` is an `f`-vector of `z` integer vectors holding the vectors of  predicted labels. There is one vector for each fold (`f`) and each containes as many vector as classes (`z`), in turn each one containing the predicted labels for the trials.

`.losses` is an `f`-vector holding BitVector types (vectors of booleans),  each holding the binary loss for a fold. 

`.cnfs` is an `f`-vector of matrices holding the *confusion matrices* obtained at each fold of the cross-validation. These matrices holds  *frequencies* (counts), that is, the sum of all elements equals the number of trials used for each fold.

`.avgCnf` is the *average confusion matrix* of proportions  across the folds of the cross-validation. This matrix holds *proportions*, that is, the sum of all elements equal 1.0.

`.accs` is an `f`-vector of real numbers holding the *accuracies* obtained at each fold of the cross-validation.

`.avgAcc` is the *average accuracy* across the folds of the cross-validation.

`.stdAcc` is the *standard deviation of the accuracy* across the folds of the cross-validation.

`.z` is the test-statistic fot the hypothesis that the observed average error loss is  inferior to the specified expected value.

`.p` is the p-value of the above hypothesis test.

See [`crval`](@ref) for more informations
