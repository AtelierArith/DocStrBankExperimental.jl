```
BACON(in_dims::Int, out_dims::Int, N::Int, period::Real; hidden_dims::Int, num_layers::Int)
```

Band-limited Coordinate Networks (BACON) from [lindell2021bacon](@cite). Similar to [`FourierFilterNet`](@ref) but the frequcies are dicrete and nontrainable.

Tips: It is recommended to set `period` to be `1,2,π` or `2π` for better performance.
