```
fits_insert_rows(f::FITSFile, firstrow::Integer, nrows::Integer)
```

行番号 `firstrow` の後に `nrows` と等しい数の行を挿入します。

各行の要素はデフォルト値で初期化されます：後で [`fits_write_col`](@ref) を使用して変更できます。

最初の行は位置1にあるため、最初の行の前に行を挿入するには、`firstrow` をゼロにする必要があります。
