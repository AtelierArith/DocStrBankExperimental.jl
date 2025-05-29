```
fit(
    ::Type{M},
    X::AbstractMatrix{T},
    y::AbstractVector{T},
    est::AbstractMEstimator;
    method::Symbol       = :auto,  # :chol, :qr, :cg
    dofit::Bool          = true,
    wts::FPVector        = similar(y, 0),
    offset::FPVector     = similar(y, 0),
    fitdispersion::Bool  = false,
    ridgeλ::Real         = 0,
    ridgeG::Union{UniformScaling, AbstractArray} = I,
    βprior::AbstractVector = [],
    quantile::Union{Nothing, AbstractFloat} = nothing,
    dropcollinear::Bool = false,
    initial_scale::Union{Symbol, Real}=:mad,
    σ0::Union{Nothing, Symbol, Real}=initial_scale,
    initial_coef::AbstractVector=[],
    β0::AbstractVector=initial_coef,
    correct_leverage::Bool=false,
    fitargs...,
) where {M<:RobustLinearModel, T<:AbstractFloat}
```

Create a robust model with the model matrix (or formula) X and response vector (or dataframe) y, using a robust estimator.

# Arguments

  * `X`: the model matrix (it can be dense or sparse) or a formula
  * `y`: the response vector or a table (dataframe, namedtuple, ...).
  * `est`: a robust estimator

# Keywords

  * `method::Symbol = :auto`: the method to use for solving the weighted linear system,   `chol` (default), `qr` or `cg`. Use :auto to select the default method;
  * `dofit::Bool = true`: if false, return the model object without fitting;
  * `dropmissing::Bool = false`: if true, drop the rows with missing values (and convert to   Non-Missing type). With `dropmissing=true` the number of observations may be smaller than   the size of the input arrays;
  * `wts::Vector = similar(y, 0)`: Prior probability weights of observations.   Can be empty (length 0) if no weights are used (default);
  * `offset::Vector = similar(y, 0)`: an offset vector, should be empty if no offset is used;
  * `fitdispersion::Bool = false`: reevaluate the dispersion;
  * `ridgeλ::Real = 0`: if positive, perform a robust ridge regression with shrinkage   parameter `ridgeλ`. [`RidgePred`](@ref) object will be used;
  * `ridgeG::Union{UniformScaling, AbstractArray} = I`: define a custom regularization matrix.   Default to unity matrix (with 0 for the intercept);
  * `βprior::AbstractVector = []`: define a custom prior for the coefficients for ridge regression.   Default to `zeros(p)`;
  * `quantile::Union{Nothing, AbstractFloat} = nothing`:   only for [`GeneralizedQuantileEstimator`](@ref), define the quantile to estimate;
  * `dropcollinear::Bool=false`: controls whether or not a model matrix less-than-full rank is   accepted;
  * `contrasts::AbstractDict{Symbol,Any} = Dict{Symbol,Any}()`: a `Dict` mapping term names   (as `Symbol`s) to term types (e.g. `ContinuousTerm`) or contrasts (e.g., `HelmertCoding()`,   `SeqDiffCoding(; levels=["a", "b", "c"])`, etc.). If contrasts are not provided for a variable,   the appropriate term type will be guessed based on the data type from the data column:   any numeric data is assumed to be continuous, and any non-numeric data is assumed to be   categorical (with `DummyCoding()` as the default contrast type);
  * `initial_scale::Union{Symbol, Real}=:mad`: the initial scale estimate, for non-convex estimator   it helps to find the global minimum. Automatic computation using `:mad`, `L1` or   `extrema` (non-robust).
  * `σ0::Union{Nothing, Symbol, Real}=initial_scale`: alias of `initial_scale`;
  * `initial_coef::AbstractVector=[]`: the initial coefficients estimate, for non-convex estimator   it helps to find the global minimum.
  * `β0::AbstractVector=initial_coef`: alias of `initial_coef`;
  * `correct_leverage::Bool=false`: apply the leverage correction weights with   [`leverage_weights`](@ref).
  * `fitargs...`: other keyword arguments used to control the convergence of the IRLS algorithm   (see [`RobustModels.pirls!`](@ref)).

# Output

the RobustLinearModel object.
