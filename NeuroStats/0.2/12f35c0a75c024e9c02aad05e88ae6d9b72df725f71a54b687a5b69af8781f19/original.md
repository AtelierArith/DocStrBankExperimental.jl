```
cor_test(seg1, seg2)
```

Calculate correlation between two vectors.

# Arguments

  * `s1::AbstractVector`
  * `s2::AbstractVector`

# Returns

Named tuple containing:

  * `t::CorrelationTest{Float64}`
  * `r::Float64`: correlation coefficient
  * `rc::Tuple{Float64, Float64}`: correlation coefficient confidence interval
  * `ts::Tuple{Float64, String}`: t-statistics
  * `df::Int64`: degrees of freedom
  * `p::Float64`: p value
