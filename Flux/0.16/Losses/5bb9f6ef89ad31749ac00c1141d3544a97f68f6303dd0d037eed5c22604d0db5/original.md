```
squared_hinge_loss(ŷ, y)
```

Return the squared hinge_loss loss given the prediction `ŷ` and true labels `y` (containing 1 or -1); calculated as

```
sum((max.(0, 1 .- ŷ .* y)).^2) / size(y, 2)
```

Usually used with classifiers like Support Vector Machines. See also: [`hinge_loss`](@ref)

# Example

```jldoctes
julia> y_true = [1, -1, 1, 1];

julia> y_pred = [0.1, 0.3, 1, 1.5];

julia> Flux.squared_hinge_loss(y_pred, y_true)
0.625

julia> Flux.squared_hinge_loss(y_pred[1], y_true[1]) != 0
true

julia> Flux.squared_hinge_loss(y_pred[end], y_true[end]) == 0
true

julia> Flux.squared_hinge_loss(y_pred[2], y_true[2]) != 0
true
```
