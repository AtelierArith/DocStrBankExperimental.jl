```
mae(ŷ, y; agg = mean)
```

Return the loss corresponding to mean absolute error:

```
agg(abs.(ŷ .- y))
```

# Example

```jldoctest
julia> y_model = [1.1, 1.9, 3.1];

julia> Flux.mae(y_model, 1:3)
0.10000000000000009
```
