```
format_color_gradient!(client::GoogleSheetsClient, range::CellIndexRange2D; 
    min_color::Colorant=colorant"salmon", min_value_type::ValueType=VALUE_TYPE_MIN, min_value::Union{Nothing,Number}=nothing, 
    mid_color::Union{Nothing,Colorant}=nothing, mid_value_type::Union{Nothing,ValueType}=nothing, mid_value::Union{Nothing,Number}=nothing, 
    max_color::Colorant=colorant"springgreen", max_value_type::ValueType=VALUE_TYPE_MAX, max_value::Union{Nothing,Number}=nothing)::Dict{Any,Any}
```

カラーグラデーションの書式設定を設定します。

# 引数

  * `client::GoogleSheetsClient`: クライアント。
  * `range::CellIndexRange2D`: セルインデックス範囲。
  * `min_color::Colorant=colorant"salmon"`: 最小値の色。
  * `min_value_type::ValueType=VALUE_TYPE_MIN`: 最小値のタイプ。
  * `min_value::Union{Nothing,Number}=nothing`: 最小値。
  * `mid_color::Union{Nothing,Colorant}=nothing`: 中間値の色。
  * `mid_value_type::Union{Nothing,ValueType}=nothing`: 中間値のタイプ。
  * `mid_value::Union{Nothing,Number}=nothing`: 中間値。
  * `max_color::Colorant=colorant"springgreen"`: 最大値の色。
  * `max_value_type::ValueType=VALUE_TYPE_MAX`: 最大値のタイプ。
  * `max_value::Union{Nothing,Number}=nothing`: 最大値。
