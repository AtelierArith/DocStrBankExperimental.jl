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

Separate items with \0 within a string, end item-list with \0\0. e.g. "One\0Two\0Three\0".

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L588).
