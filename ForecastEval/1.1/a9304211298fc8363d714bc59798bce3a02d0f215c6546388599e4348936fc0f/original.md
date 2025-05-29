```
SPATest(rejH0::Int, mu_u::Vector{Float64}, mu_c::Vector{Float64}, mu_l::Vector{Float64}, pvalue_u::Float64, pvalue_c::Float64, pvalue_l::Float64, pvalue::Float64, teststat::Float64)
```

Output type for an SPA test proposed in Hansen (2005) "A Test for Superior Predictive Ability". The names of the fields for this type follow those in the referenced paper, so see that paper for more detail. The fields of this type follow: 

```
rejH0 <- true if the null is rejected, false otherwise
mu_u <- mu associated with upper bound on threshold rate
mu_c <- Recommended mu
mu_l <- mu associated with lower bound on threshold rate
pvalue_u <- pvalue associated with mu_u
pvalue_c <- pvalue assoicated with mu_c
pvalue_l <- pvalue associated with mu_l
pvalueauto <- Recommended p-value (usually pvalue_c except in rare situations where this method can fail)
teststat::Float64 <- SPA test statistic (look for tSPA in source paper)
```

Note the different mu variables, {u, c, l} are described in the referenced article on p370-371. 

Most users will just be interested in the field pvalueauto.
