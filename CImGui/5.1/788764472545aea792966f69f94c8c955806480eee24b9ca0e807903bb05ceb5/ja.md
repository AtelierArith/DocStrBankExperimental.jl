```julia
BeginPopupContextItem() -> Bool
BeginPopupContextItem(str_id) -> Bool
BeginPopupContextItem(
    str_id,
    popup_flags::Union{CImGui.lib.ImGuiPopupFlags_, Integer}
) -> Bool

```

最後のアイテムをクリックしたときにポップアップを開いて開始します。str_id==NULLを使用してポップアップを前のアイテムに関連付けます。Text()のような非対話型アイテムでそれを使用したい場合は、ここで明示的なIDを渡す必要があります。 .cppのコメントを読んでください！

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L793).
