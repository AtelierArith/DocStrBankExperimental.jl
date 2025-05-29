```
Population(X::AbstractMatrix{T}, y::AbstractVector{T};
           population_size, nlength::Int=3,
           options::AbstractOptions, nfeatures::Int,
           loss_type::Type=Nothing)
```

Create random population and score them on the dataset.
