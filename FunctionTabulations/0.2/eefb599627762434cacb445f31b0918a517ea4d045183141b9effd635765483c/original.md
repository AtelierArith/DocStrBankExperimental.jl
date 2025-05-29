```
create_tabulation_1D(
    func::Function,
    x::Vector{T},
    args...;
    jld_base_path = nothing,
    custom_name = nothing,
    x_scale::Symbol = :linear,
    f_scale = :linear,
    interpolation_type = :linear,
    extrapolation_bc = Throw,
    check_SHA = true,
    check_SHA_mode = :warn,
    metadata=nothing,
    metadata_validation_fn=nothing,
    kwargs...
    ) where {T<:Union{Real,Quantity}}
```

Provides an interface for `create_tabulation_1D` where the tabulation points are defined by the Vector `x`. Only `linear_interpolation` is supported.`
