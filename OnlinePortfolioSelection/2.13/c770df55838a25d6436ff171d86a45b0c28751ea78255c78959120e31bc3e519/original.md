```
ttest(vec::AbstractVector{<:AbstractVector})
ttest(SB::AbstractVector, Sₜ::AbstractVector, SF::AbstractFloat)
```

# Method 1

```julia
ttest(vec::AbstractVector{<:AbstractVector})
```

Perform a one sample t-test of the null hypothesis that `n` values with mean `x̄` and sample standard deviation stddev come from a distribution with mean $μ_0$ against the alternative hypothesis that the distribution does not have mean $μ_0$. The t-test with 95% confidence level applies on each pair of vectors in the `vec` vector. Each vector should contain the Annual Percentage Yield (APY) of a different algorithm on various datasets.

!!! note
    You have to install and import the `HypothesisTests` package to use this function.


## Arguments

  * `vec::AbstractVector{<:AbstractVector}`: A vector of vectors. Each inner vector should be of the same size.

## Returns

  * `::Matrix{<:AbstractFloat}`: A matrix of p-values for each pair of algorithms.

## Example

```julia
julia> using OnlinePortfolioSelection, HypothesisTests

julia> apys = [
         [1, 2, 3, 4],
         [2, 7, 0, 1],
         [3, 0, 0, 5]
       ];

julia> ttest(apys)
3×3 Matrix{Float64}:
 0.0  1.0  0.702697
 0.0  0.0  0.843672
 0.0  0.0  0.0
```

# Method 2

```julia
ttest(SB::AbstractVector, Sₜ::AbstractVector, SF::AbstractFloat)
```

Performs a t-student test to check whether the returns gained by a trading algorithm is due to a simple luck.

!!! note
    You have to install and import the `GLM` package to use this function.


## Arguments

  * `SB::AbstractVector`: Denotes the daily returns of the benchmark (market index)
  * `Sₜ::AbstractVector`: Portfolio daily returns
  * `SF::AbstractFloat`: Daily returns of the risk-free assets (Can be set to Treasury bill value or annual interest rate.)
  * `::StatsModels.TableRegressionModel`: An object of type `TableRegressionModel` including the values of t-student test analysis.
