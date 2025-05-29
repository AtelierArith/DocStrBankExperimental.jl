```
WarpedView(img, tform, [indices]; kwargs...) -> wv
```

`img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を遅延的に変換します。したがって、`wv[I] == img[tform(I)]`となります。

これは`warp`の遅延ビュー版です。詳細については[`warp`](@ref)を参照してください。
