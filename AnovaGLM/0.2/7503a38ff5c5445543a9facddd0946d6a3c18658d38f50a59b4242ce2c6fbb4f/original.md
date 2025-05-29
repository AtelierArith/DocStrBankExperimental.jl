```
anova_glm(X, y, d::UnivariateDistribution, l::Link = canonicallink(d); 
        test::Type{<: GoodnessOfFit} = canonicalgoodnessoffit(d), <keyword arguments>)

anova_glm(test::Type{<: GoodnessOfFit}, X, y, d::UnivariateDistribution, l::Link = canonicallink(d); <keyword arguments>)

anova(test::Type{<: GoodnessOfFit}, X, y, d::UnivariateDistribution, l::Link = canonicallink(d); <keyword arguments>)
```

ANOVA for genaralized linear models.

# Arguments

  * `X` and `y` can be a `Matrix` and a `Vector` or a `Formula` and a `Tables.jl` compatible data.
  * `d`: a `GLM.UnivariateDistribution`.
  * `l`: a `GLM.Link`
  * `test`: test statistics for goodness of fit based on distribution function. See `canonicalgoodnessoffit`.

For other keyword arguments, see `fit`.
