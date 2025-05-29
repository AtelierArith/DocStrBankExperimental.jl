```
ransac(setting; t, w=0.5, m=0, k=0, d=0, confidence=0.99)
```

Run the RANSAC (1981) algorithm for the given regression setting

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and a dataset.
  * `t::Float64`: The threshold distance of a sample point to the regression hyperplane to determine if it fits the model well.
  * `w::Float64`: The probability of a sample point being inlier, default=0.5.
  * `m::Int`: The number of points to sample to estimate the model parameter for each iteration. If set to 0, defaults to picking p points which is the minimum required.
  * `k::Int`: The number of iterations to run. If set to 0, is calculated according to the formula given in the paper based on outlier probability and the sample set size.
  * `d::Int`: The number of close data points required to accept the model. Defaults to number of data points multiplied by inlier ratio.
  * `confidence::Float64`: Required to determine the number of optimum iterations if k is not specified.

# Output

  * `["outliers"]`: Array of indices of outliers.

# Examples

```julia-repl
julia> df = DataFrame(y=[0,1,2,3,3,4,10], x=[0,1,2,2,3,4,2])
julia> reg = createRegressionSetting(@formula(y ~ x), df)
julia> ransac(reg, t=0.8, w=0.85)
Dict{String,Array{Int64,1}} with 1 entry:
  "outliers" => [7]
```

# References

Martin A. Fischler & Robert C. Bolles (June 1981). "Random Sample Consensus: A Paradigm for Model Fitting with Applications to Image Analysis and Automated Cartography" Comm. ACM. 24 (6): 381–395.
