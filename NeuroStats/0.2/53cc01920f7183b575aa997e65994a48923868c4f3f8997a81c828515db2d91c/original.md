```
cmp_test(seg1, seg2; <keyword arguments>)
```

Compare two vectors. Jarque–Bera is used first to test normality of distribution, next variances are tested using F-test. Finally, paired or non-paired t-test or non-parametric test (Wilcoxon signed rank for paired data; Mann-Whitney U test for non-paired data) is applied. Permutation-based testing is also 

# Arguments

  * `s1::AbstractVector`
  * `s2::AbstractVector`
  * `paired::Bool`
  * `alpha::Float64=0.05`: confidence level
  * `type::Symbol=:auto`

      * `:auto`: choose test automatically
      * `:perm`: permutation-based
      * `:p`: parametric
      * `:np`: non-parametric
  * `exact::Bool=false`: if true, use exact Wilcoxon test
  * `nperm::Int64=1000`: number of permutation for `:perm` method
  * `verbose::Bool=true`: print detailed output

# Returns

For permutation-based test, named tuple containing:

  * `t::Tuple{perm_diff::Vector{Float64}, obs_diff::Float64}`: test result (permutation difference, observed difference)
  * `p1::Float64`: one-tiled p value
  * `p2::Float64`: two-tiled p value

Otherwise, named tuple containing:

  * `t::Union{OneSampleTTest, EqualVarianceTTest, UnequalVarianceTTest, ExactSignedRankTest, ApproximateSignedRankTest, ExactMannWhitneyUTest, ApproximateMannWhitneyUTest}`: statistical test
  * `ts::Tuple{Float64, String}`: test statistic value and name
  * `tc::Tuple{Float64, Float64}`: test statistic confidence interval
  * `df::Float64`: degrees of freedom
  * `p::Float64`: p value
