```
hinge_loss(ŷ, y; agg = mean)
```

Return the [hinge_loss](https://en.wikipedia.org/wiki/Hinge_loss) given the prediction `ŷ` and true labels `y` (containing 1 or -1); calculated as

```
sum(max.(0, 1 .- ŷ .* y)) / size(y, 2)
```

Usually used with classifiers like Support Vector Machines. See also: [`squared_hinge_loss`](@ref)

# Example

```jldoctest
julia> y_true = [1, -1, 1, 1];

julia> y_pred = [0.1, 0.3, 1, 1.5];

julia> Flux.hinge_loss(y_pred, y_true)
0.55

julia> Flux.hinge_loss(y_pred[1], y_true[1]) != 0  # same sign but |ŷ| < 1
true

julia> Flux.hinge_loss(y_pred[end], y_true[end]) == 0  # same sign but |ŷ| >= 1
true

julia> Flux.hinge_loss(y_pred[2], y_true[2]) != 0 # opposite signs
true
```
