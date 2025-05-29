```julia
PushID(
    str_id_begin::Union{Ptr{Int8}, String},
    str_id_end::Union{Ptr{Int8}, Ptr{Nothing}, String}
)

```

IDスタックに文字列をプッシュします（文字列をハッシュします）。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L532).
