```
anova_lm(X, y; test::Type{<: GoodnessOfFit} = FTest, <keyword arguments>) 

anova_lm(test::Type{<: GoodnessOfFit}, X, y; <keyword arguments>)

anova(test::Type{<: GoodnessOfFit}, ::Type{LinearModel}, X, y; 
    type::Int = 1, 
    <keyword arguments>)
```

ANOVA for simple linear regression.

# Arguments

  * `X` and `y` can be a `Matrix` and a `Vector` or a `Formula` and a `Tables.jl` compatible data.
  * `test`: test statistics for goodness of fit.

# Keyword arguments

  * `test`: test statistics for goodness of fit.
  * `type` specifies type of anova (1, 2 or 3). Default value is 1.
  * `dropcollinear` controls whether or not `lm` accepts a model matrix which is less-than-full rank. If true (the default), only the first of each set of linearly-dependent columns is used. The coefficient for redundant linearly dependent columns is 0.0 and all associated statistics are set to NaN.

`anova_lm` generate a `TableRegressionModel` object, which is fitted by `lm`.
