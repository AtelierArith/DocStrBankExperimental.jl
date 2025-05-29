```julia
ListBox(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items::Vector{String}
) -> Bool
ListBox(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    current_item::Union{Ptr{Nothing}, Ref{Int32}},
    items::Vector{String},
    height_in_items::Integer
) -> Bool

```

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L713).
