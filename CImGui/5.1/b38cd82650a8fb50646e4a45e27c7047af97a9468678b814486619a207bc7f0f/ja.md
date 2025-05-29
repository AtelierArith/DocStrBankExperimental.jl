```julia
GetID(str_id::Union{Ptr{Int8}, String}) -> UInt32

```

ユニークIDを計算します（全IDスタックのハッシュ + 与えられたパラメータ）。例えば、ImGuiStorageに自分でクエリを行いたい場合。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L536).
