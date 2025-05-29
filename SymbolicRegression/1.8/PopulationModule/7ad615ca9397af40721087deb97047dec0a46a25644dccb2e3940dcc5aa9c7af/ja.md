```
Population(X::AbstractMatrix{T}, y::AbstractVector{T};
           population_size, nlength::Int=3,
           options::AbstractOptions, nfeatures::Int,
           loss_type::Type=Nothing)
```

ランダムな集団を作成し、データセット上でスコアを付けます。
