```
mJy_to_W(S::Union{Real, Unitful.AbstractQuantity}, h::AbstractGadgetHeader)
```

与えられた赤方偏移と `AbstractGadgetHeader` から取得した宇宙論に対して、シンクロトロンフラックス密度 `S` を `[mJy]` から `[W/Hz]` に変換します。
