```
testmode!(model, [mode]) -> model
```

Set a layer, or all layers in a model, to test mode. This disables the effect of [`Dropout`](@ref) and some other regularisation layers.

If you manually set a model into test mode, you need to manually place it back into train mode during training phase, using [`trainmode!`](@ref).

There is an optional second argument, which takes a symbol `:auto` to reset all layers back to the default automatic mode.

# Example

```jldoctest
julia> d = Dropout(0.3)
Dropout(0.3)

julia> testmode!(d)   # dropout is now always disabled
Dropout(0.3, active=false)

julia> trainmode!(d)  # dropout is now always enabled
Dropout(0.3, active=true)

julia> testmode!(d, :auto)  # back to default
Dropout(0.3)
```
