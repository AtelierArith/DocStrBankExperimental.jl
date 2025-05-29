```julia
Combo(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items_separated_by_zeros::Union{Ptr{Int8}, String}
) -> Bool
Combo(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items_separated_by_zeros::Union{Ptr{Int8}, String},
    popup_max_height_in_items::Integer
) -> Bool

```

文字列内のアイテムを\0で区切り、アイテムリストの終わりを\0\0で示します。例: "One\0Two\0Three\0"。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L588).
