```
predict_proba{V<:Number}(m::HybridNB, f_c::Vector{Vector{Float64}}, f_d::Vector{Vector{Int64}})
```

Predict log-probabilities for the input features. Returns tuples of predicted class and its log-probability estimate.
