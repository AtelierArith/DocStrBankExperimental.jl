```
confint(r::AbstractDIDResult; level::Real=0.95)
```

Return a confidence interval for each coefficient estimate. The returned object is of type `Tuple{Vector{Float64}, Vector{Float64}}` where the first vector collects the lower bounds for all intervals and the second one collects the upper bounds.
