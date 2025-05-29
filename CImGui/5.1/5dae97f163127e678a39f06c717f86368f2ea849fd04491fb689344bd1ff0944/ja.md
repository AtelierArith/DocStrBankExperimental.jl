```julia
TableGetColumnFlags() -> Int32
TableGetColumnFlags(column_n) -> Int32

```

列のフラグを返し、Enabled/Visible/Sorted/Hovered ステータスフラグを照会できます。現在の列を使用するには -1 を渡してください。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L855).
