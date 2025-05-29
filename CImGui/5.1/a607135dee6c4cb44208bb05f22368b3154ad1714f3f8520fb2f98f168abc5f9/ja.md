```julia
TreeNode(
    str_id::Union{Ptr{Int8}, String},
    fmt::Union{Ptr{Int8}, Ptr{Nothing}, String}
) -> Bool

```

IDを表示された文字列から簡単にデコレートするためのヘルパーのバリエーション。IDの使用方法と理由についてはFAQを参照してください。TreeNode()と同じレベルで任意のテキストを整列させるには、Bullet()を使用できます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L668).
