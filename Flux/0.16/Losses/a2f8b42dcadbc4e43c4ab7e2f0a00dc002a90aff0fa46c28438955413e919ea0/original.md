```
huber_loss(ŷ, y; delta = 1, agg = mean)
```

Return the mean of the [Huber loss](https://en.wikipedia.org/wiki/Huber_loss) given the prediction `ŷ` and true values `y`.

```
             | 0.5 * |ŷ - y|^2,            for |ŷ - y| <= δ
Huber loss = |
             |  δ * (|ŷ - y| - 0.5 * δ), otherwise
```

# Example

```jldoctest
julia> ŷ = [1.1, 2.1, 3.1];

julia> Flux.huber_loss(ŷ, 1:3)  # default δ = 1 > |ŷ - y|
0.005000000000000009

julia> Flux.huber_loss(ŷ, 1:3, delta=0.05)  # changes behaviour as |ŷ - y| > δ
0.003750000000000005
```
