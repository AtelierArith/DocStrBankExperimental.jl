```julia
TextUnformatted(text)
TextUnformatted(text, text_end)

```

フォーマットなしの生テキスト。Text("%s", text)とほぼ同等ですが、A) 'text_end'が指定されている場合、ヌル終端文字列を必要としません。B) より高速で、メモリコピーは行われず、バッファサイズの制限もありません。長いテキストの塊には推奨されます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L542).
