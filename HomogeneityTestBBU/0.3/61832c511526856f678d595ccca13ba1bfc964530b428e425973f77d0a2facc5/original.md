```
homogeneity_test_fn
```

This function implements the homogeneity test of Bugni, Bunting and Ura (2023).

## Arguments

  * `X::Tuple`: The data in the form of tuple $X=(S, A)$, where A may be empty.
  * `test_stat_fn::Function`: A function that takes the arguments $S$ and $A$ (or $S$ only, if $A=[~]$) and returns a (vector of) test statistics.
  * `K::Int`: An integer indicating the length of the MCMC chain. Defaults to 10,000.
  * `verbose::Vector{String}`: Possible elements of the vector are `"P value"`, `"Test stat"`, and `"X^K"`. Defaults to empty.
  * `A_trivial::Boolean`: A Boolean indicating whether $S'=A$. Defaults to false.

## Values

  * `Pvalue`: The test's p-value (Bugni, Bunting and Ura (2023), equation (4)).
  * `Pvalue_chain`: The p-value computed at each of $K$ steps (optional).
  * `test_stat_chain`: The test statistic computed on $X$ and of $K$ steps (optional).
  * `X_K': The tuple containing the the permuted data (optional).
