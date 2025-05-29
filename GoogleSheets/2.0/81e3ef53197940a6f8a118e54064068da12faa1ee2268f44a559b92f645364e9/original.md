```
format_color_gradient!(client::GoogleSheetsClient, range::CellIndexRange2D; 
    min_color::Colorant=colorant"salmon", min_value_type::ValueType=VALUE_TYPE_MIN, min_value::Union{Nothing,Number}=nothing, 
    mid_color::Union{Nothing,Colorant}=nothing, mid_value_type::Union{Nothing,ValueType}=nothing, mid_value::Union{Nothing,Number}=nothing, 
    max_color::Colorant=colorant"springgreen", max_value_type::ValueType=VALUE_TYPE_MAX, max_value::Union{Nothing,Number}=nothing)::Dict{Any,Any}
```

Sets color gradient formatting.

# Arguments

  * `client::GoogleSheetsClient`: client.
  * `range::CellIndexRange2D`: cell index range.
  * `min_color::Colorant=colorant"salmon"`: color for the minimum value.
  * `min_value_type::ValueType=VALUE_TYPE_MIN`: minimum value type.
  * `min_value::Union{Nothing,Number}=nothing`: minimum value.
  * `mid_color::Union{Nothing,Colorant}=nothing`: color for the mid value.
  * `mid_value_type::Union{Nothing,ValueType}=nothing`: mid value type.
  * `mid_value::Union{Nothing,Number}=nothing`: mid value.
  * `max_color::Colorant=colorant"springgreen"`: color for the maximum value.
  * `max_value_type::ValueType=VALUE_TYPE_MAX`: maximum value type.
  * `max_value::Union{Nothing,Number}=nothing`: maximum value.
