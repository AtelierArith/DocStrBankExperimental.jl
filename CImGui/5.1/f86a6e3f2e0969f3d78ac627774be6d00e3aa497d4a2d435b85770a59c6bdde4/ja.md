```julia
RadioButton(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    v::Union{Ptr{Nothing}, Ref{Int32}},
    v_button::Integer
) -> Bool

```

整数値の場合に上記のパターンを処理するためのショートカットです。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L568).
