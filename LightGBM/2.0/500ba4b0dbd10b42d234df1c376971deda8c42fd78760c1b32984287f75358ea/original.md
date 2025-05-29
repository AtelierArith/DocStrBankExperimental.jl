```
fit!(
estimator::LGBMEstimator, 
X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, 
y::Vector{Ty}, 
test::Tuple{Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, Vector{Ty}}...;
verbosity::Integer = 1,
is_row_major = false,
weights::Vector{Tw} = Float32[],
init_score::Vector{Ti} = Float64[],
group::Vector{Int} = Int[],
truncate_booster::Bool=true,
```

) where {TX<:Real,Ty<:Real,Tw<:Real,Ti<:Real}     fit!(estimator, X, y[, test...]; [verbosity = 1, is*row*major = false])     fit!(estimator, X, y, train*indices[, test*indices...]; [verbosity = 1, is*row*major = false])     fit!(estimator, train*dataset[, test*datasets...]; [verbosity = 1])

Fit the `estimator` with features data `X` and label `y` using the X-y pairs in `test` as validation sets. Alternatively, Fit the `estimator` with `train_dataset` and `test_datasets` in the form of Dataset class(es)

Return a dictionary with an entry for each validation set. Each entry of the dictionary is another dictionary with an entry for each validation metric in the `estimator`. Each of these entries is an array that holds the validation metric's value at each iteration.

## Positional Arguments

  * `estimator::LGBMEstimator`: the estimator to be fit.
  * and either

      * `X::Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}`: the features data. May be a `SparseArrays.SparseMatrixCSC`

    If `X` is of type `Union{Float, Missing}`, missing values will be replaced with `NaN`.   If `X` is of type `Int`, missing values will be replaced with `NaN` after casting to `Float64`.

      * `y::Vector{Ty<:Real}`: the labels.
      * `test::Tuple{Union{AbstractMatrix{TX}, AbstractMatrix{Union{TX, Missing}}}, Vector{Ty}}...`: (optional)    contains one or more tuples of X-y pairs of the same types as `X` and `y` that should be used as validation sets.    May be a `SparseArrays.SparseMatrixCSC` and contain missing values.    Supports mix-and-match sparse/dense among these test and the train.
  * or

      * `train_dataset::Dataset`: prepared train_dataset
      * `test_datasets::Vector{Dataset}`: (optional) prepared test_datasets
  * or

      * `train_filepath::String`: path to the training data file.
      * `test_filepath::String`: (optional) path to the test data file.

## Keyword Arguments

  * `verbosity::Integer`: keyword argument that controls LightGBM's verbosity. `< 0` for fatal logs   only, `0` includes warning logs, `1` includes info logs, and `> 1` includes debug logs.
  * `is_row_major::Bool`: keyword argument that indicates whether or not `X` is row-major. `true`   indicates that it is row-major, `false` indicates that it is column-major (Julia's default).   Should be consistent across train/test. Does not apply to `SparseArrays.SparseMatrixCSC` or `Dataset` constructors.
  * `weights::Vector{Tw<:Real}`: the training weights.
  * `init_score::Vector{Ti<:Real}`: the init scores.
  * `group::Vector{Int}`: group size information for ranking tasks.
  * `truncate_booster::Bool`: allows to reduce the size of the model by removing less impactful trees. Default is `true`.
