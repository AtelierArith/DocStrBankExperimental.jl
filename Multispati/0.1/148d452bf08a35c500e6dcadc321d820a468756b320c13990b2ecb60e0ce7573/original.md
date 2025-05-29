```
predict(M::MULTISPATI, x::AbstractVecOrMat{<:Real})
```

Transform the observations `x` with the model `M`.

Here, `x` can be either a vector of length `d` or a matrix where each column is an observation.
