```
function create_tabulation_3D(
    func::Function,
    x::Vector{T},
    y::Vector{V},
    z::Vector{W},
    args...;
    jld_base_path = nothing,
    custom_name = nothing,
    x_scale::Symbol = :linear,
    y_scale::Symbol = :linear,
    z_scale::Symbol = :linear,
    f_scale = :linear,
    interpolation_type = :linear,
    extrapolation_bc = Throw,
    check_SHA = true,
    check_SHA_mode = :warn,
    metadata=nothing,
    metadata_validation_fn=nothing,
    kwargs...
) where {T<:Union{Real,Quantity},V<:Union{Real,Quantity},W<:Union{Real,Quantity}}
```

Provides an interface for `create_tabulation_3D` where the tabulation points are defined by the Vectors `x`, `y` and `z`. Only `linear_interpolation` is supported.`
