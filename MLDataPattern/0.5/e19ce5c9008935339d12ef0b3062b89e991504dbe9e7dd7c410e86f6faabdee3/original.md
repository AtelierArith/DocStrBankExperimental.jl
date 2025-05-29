```
FoldsView(data, train_indices, val_indices, [obsdim])
```

# Description

Create a vector-like representation of `data` where each individual element is partition of `data` in the form of a tuple of two data subsets (a training- and a validation subset).

The purpose of `FoldsView` is to apply a precomputed sequence of subset assignment indices to some data container in a convenient manner. By itself, `FoldsView` is agnostic to any particular repartitioning strategy (such as k-folds). Instead, the assignments, `train_indices` and `val_indices`, need to be precomputed by such a strategy and then passed to `FoldsView` with a concrete `data` container. The resulting object can then be queried for its individual folds using `getindex`, or simply iterated over.

# Arguments

  * **`data`** : The object describing the dataset. Can be of any   type as long as it implements [`getobs`](@ref) and   [`nobs`](@ref) (see Details for more information).
  * **`train_indices`** : Vector of integer vectors containing the   sequence of training assignments. This means that each   element is a vector of indices that describe each *training*   subset. The length of this vector must match `val_indices`.
  * **`val_indices`** : Vector of integer vectors containing the   sequence of validation assignments. This means that each   element is a vector of indices that describe each   *validation* subset. The length of this vector must match   `train_indices`.
  * **`obsdim`** : Optional. If it makes sense for the type of   `data`, `obsdim` can be used to specify which dimension of   `data` denotes the observations. It can be specified in a   type-stable manner as a positional argument (see   `?LearnBase.ObsDim`), or more conveniently as a smart keyword   argument.

# Details

For `FoldsView` to work on some data structure, the desired type `MyType` must implement the following interface:

  * `LearnBase.getobs(data::MyType, idx, [obsdim::ObsDimension])` :   Should return the observation(s) indexed by `idx`.   In what form is up to the user.   Note that `idx` can be of type `Int` or `AbstractVector`.
  * `StatsBase.nobs(data::MyType, [obsdim::ObsDimension])` :   Should return the total number of observations in `data`

# Author(s)

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# Examples

```
# Load iris data for demonstration purposes
X, y = MLDataUtils.load_iris()

# Compute train- and validation-partition indices using kfolds
train_idx, val_idx = kfolds(nobs(X), 10)

# These two vectors contain the indices vector for each partitioning
@assert typeof(train_idx) <: Vector{Vector{Int64}}
@assert typeof(val_idx)   <: Vector{UnitRange{Int64}}
@assert length(train_idx) == length(val_idx) == 10

# Using the repartitioning as an oterator
for (train_X, val_X) in FoldsView(X, train_idx, val_idx)
    @assert size(train_X) == (4, 135)
    @assert size(val_X) == (4, 15)
end

# Calling kfolds with the dataset will create
# the FoldsView for you automatically.
# Thus this code is equivalent to above
for (train_X, val_X) in kfolds(X, 10)
    @assert size(train_X) == (4, 135)
    @assert size(val_X) == (4, 15)
end

# leavout is a shortcut for setting k = nobs(X)
for (train_X, val_X) in leaveout(X)
    @assert size(val_X) == (4, 1)
end
```

# see also

[`kfolds`](@ref), [`leaveout`](@ref), [`splitobs`](@ref), [`DataSubset`](@ref)
