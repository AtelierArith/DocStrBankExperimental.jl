```
create_mlp(
    ninput::Int, 
    noutput::Int, 
    hiddenlayers::Tuple{Vararg{Int}}, 
    dropoutp::Union{<:AbstractFloat,Tuple{Vararg{<:AbstractFloat}}}
    )
```

Return a `mlp` with `ninput`/`noutput` as the number of input/output channels, and number of units in each layer specified in `hiddenlayers`;  'dropoutp' contains the dropout probalibities for dropout layers; it can be a single value (one dropout layer before output) or same length as the hidden layers 
