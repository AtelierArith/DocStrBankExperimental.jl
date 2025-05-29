```
function create_tabulation_2D(
    func::Function,
    x::Vector{T},
    y::Vector{V},
    args...;
    jld_base_path = nothing,
    custom_name = nothing,
    x_scale::Symbol = :linear,
    y_scale::Symbol = :linear,
    f_scale = :linear,
    interpolation_type = :linear,
    extrapolation_bc = Throw,
    check_SHA = true,
    check_SHA_mode = :warn,
    metadata=nothing,
    metadata_validation_fn=nothing,
    kwargs...
) where {T<:Union{Real,Quantity},V<:Union{Real,Quantity}}
```

`create_tabulation_2D`のインターフェースを提供し、タブレーションポイントはベクトル`x`と`y`によって定義されます。`linear_interpolation`のみがサポートされています。
