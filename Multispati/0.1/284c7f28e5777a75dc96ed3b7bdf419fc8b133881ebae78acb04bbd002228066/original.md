```
reconstruct(M::MULTISPATI, y::AbstractVecOrMat{<:Real})
```

Approximately reconstruct the observations `y` to the original space using the model `M`.

Here, `y` can be either a vector of length `p` or a matrix where each column gives the components for an observation.
