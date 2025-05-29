```julia
RadioButton(
    label::Union{Ptr{Int8}, Ptr{Nothing}, String},
    active::Bool
) -> Bool

```

Use with e.g. if (RadioButton("one", my*value==1))  my*value = 1;.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L567).
