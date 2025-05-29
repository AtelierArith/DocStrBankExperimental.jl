```
WaldWolfowitzTest(x::AbstractVector{Bool})
WaldWolfowitzTest(x::AbstractVector{<:Real})
```

Perform the Wald-Wolfowitz (or Runs) test of the null hypothesis that the given data is random, or independently sampled. The data can come as many-valued or two-valued (Boolean). If many-valued, the sample is transformed by labelling each element as above or below the median.

Implements: [`pvalue`](@ref)
