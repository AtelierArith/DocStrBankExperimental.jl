```
poisson_loss(ŷ, y; agg = mean)
```

Return how much the predicted distribution `ŷ` diverges from the expected Poisson distribution `y`; calculated as -

```
sum(ŷ .- y .* log.(ŷ)) / size(y, 2)
```

[More information.](https://peltarion.com/knowledge-center/documentation/modeling-view/build-an-ai-model/loss-functions/poisson).

# Example

```jldoctest
julia> y_model = [1, 3, 3];  # data should only take integral values

julia> Flux.poisson_loss(y_model, 1:3)
0.5023128522198171
```
