```
mJy_to_W( c::Cosmology.AbstractCosmology, S::Unitful.AbstractQuantity, z::Real )
```

与えられた赤方偏移 `z` と宇宙論 `c` に対して、シンクロトロンフラックス密度 `S` を `[mJy]` から `[W/Hz]` に変換します。単位情報を保持します。
