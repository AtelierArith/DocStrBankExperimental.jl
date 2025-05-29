```julia
TreeNode(
    str_id::Union{Ptr{Int8}, String},
    fmt::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool

```

Helper variation to easily decorelate the id from the displayed string. Read the FAQ about why and how to use ID. to align arbitrary text at the same level as a TreeNode() you can use Bullet().

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L668).
