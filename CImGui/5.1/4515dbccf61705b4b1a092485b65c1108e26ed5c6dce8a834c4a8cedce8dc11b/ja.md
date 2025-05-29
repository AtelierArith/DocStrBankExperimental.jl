```julia
Combo(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items::Vector{String}
) -> Bool
Combo(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items::Vector{String},
    popup_max_height_in_items::Integer
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L587).
