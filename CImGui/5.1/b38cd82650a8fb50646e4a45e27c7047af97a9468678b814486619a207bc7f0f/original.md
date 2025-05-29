```julia
GetID(str_id::Union{Ptr{Int8}, String}) -> UInt32

```

Calculate unique ID (hash of whole ID stack + given parameter). e.g. if you want to query into ImGuiStorage yourself.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L536).
