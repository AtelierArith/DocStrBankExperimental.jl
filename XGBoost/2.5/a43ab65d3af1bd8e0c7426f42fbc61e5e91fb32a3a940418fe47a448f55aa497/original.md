```
DMatrix <: AbstractMatrix{Union{Missing,Float32}}
```

Data structure for storing data which can be understood by an xgboost [`Booster`](@ref). These can store both features and targets.  Values of the `DMatrix` can be accessed as with any other `AbstractMatrix`, however doing so causes additional allocations.  Performant indexing and matrix operation code should not use `DMatrix` directly.

Aside from a primary array, the `DMatrix` object can have various "info" fields associated with it. Training target variables are stored as a special info field with the name `label`, see [`setinfo!`](@ref) and [`setinfos!`](@ref).  These can be retrieved with [`getinfo`](@ref) and [`getlabel`](@ref).

Note that the xgboost library internally uses `Float32` to represent all data, so input data is automatically copied unless provided in this format.  Unfortunately because of the different representations used by C and Julia, any non `Transpose` matrix will also be copied.

### On `missing` Values

Xgboost supports training on `missing` data.  Such data is simply omitted from tree splits.  Because the `DMatrix` is internally a `Float32` matrix, `libxgboost` uses a settable default value to represent missing values, see the `missing_value` keyword argument below (default `NaN32`).  This value is used only on matrix construction.  This will cause input matrix elements to ultimately be converted to `missing`.  The most obvious consequence of this is that `NaN32` values will automatically be converted to `missing` with default arguments.  The provided constructors ensure that `missing` values will be preserved.

TL;DR: `DMatrix` supports `missing` and `NaN`'s will be converted to `missing`.

## Constructors

```julia
DMatrix(X::AbstractMatrix; kw...)
DMatrix(X::AbstractMatrix, y::AbstractVector; kw...)
DMatrix((X, y); kw...)
DMatrix(tbl; kw...)
DMatrix(tbl, y; kw...)
DMatrix(tbl, yname::Symbol; kw...)
```

## Arguments

  * `X`: A matrix that is the primary data wrapped by the `DMatrix`.  Elements can be `missing`.   Matrices with `Float32` eleemnts do not need to be copied.
  * `y`: Data to assign to the `label` info field.  This is the target variable used in training.   Can also be set with the `label` keyword.
  * `tbl`: The input matrix in tabular form.  `tbl` must satisfy the Tables.jl interface.   If data is passed in tabular form feature names will be set automatically but can   be overriden with the keyword argument.
  * `yname`: If passed a tabular argument `tbl`, `yname` is the name of the column which holds the   label data.  It will automatically be omitted from the features.

### Keyword Arguments

  * `missing_value`: The `Float32` value of elements of input data to be interpreted as `missing`,   defaults to `NaN32`.
  * `label`: Training target data, this is the same as the `y` argument above, i.e.   `DMatrix(X,y)` and `DMatrix(X, label=y)` are equivalent.
  * `weight`: An `AbstractVector` of weights for each data point.  This array must have lenght   equal to the number of rows of the main data matrix.
  * `base_margin`: Sets the global bias for a boosted model trained on this dataset, see   https://xgboost.readthedocs.io/en/stable/prediction.html#base-margin

## Examples

```julia
(X, y) = (randn(10,3), randn(10))

# the following are all equivalent
DMatrix(X, y)
DMatrix((X, y))
DMatrix(X, label=y)

DMatrix(X, y, feature_names=["a", "b", "c"])  # explicitly set feature names

df = DataFrame(A=randn(10), B=randn(10))
DMatrix(df)  # has feature names ["A", "B"] but no label
```
