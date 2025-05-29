```
add_axis!(
    daf::DafWriter,
    axis::AbstractString,
    entries::AbstractVector{<:AbstractString}
)::Nothing
```

新しい `axis` を `daf` に追加します。

最初に `axis` が存在しないことと、`entries` がユニークであることを確認します。
