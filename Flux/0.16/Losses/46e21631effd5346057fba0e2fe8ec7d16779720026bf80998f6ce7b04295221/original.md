```
mse(ŷ, y; agg = mean)
```

Return the loss corresponding to mean square error:

```
agg((ŷ .- y) .^ 2)
```

See also: [`mae`](@ref), [`msle`](@ref), [`crossentropy`](@ref).

# Example

```jldoctest
julia> y_model = [1.1, 1.9, 3.1];

julia> y_true = 1:3;

julia> Flux.mse(y_model, y_true)
0.010000000000000018
```
