```
insertcols!(gl::GridLayout, at::Integer, n::Integer; colsizes=nothing, addedcolgaps=nothing)
```

`GridLayout` `gl` に列 `at` で `n` 列を挿入します。新しい列のサイズと列の隙間は、オプションで `colsizes` と `addedcolgaps` キーワードを使って設定できます。少なくとも `at-1` から `at` 以上にまたがるオブジェクトは、新しい列にまたがるように拡張されます。`at` 以降のオブジェクトは後ろに押し出され、`at` より前のオブジェクトには影響がありません。
