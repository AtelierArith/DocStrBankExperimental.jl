```
NMRData <: AbstractNMRData
NMRData(A::AbstractArray{T,N}, dims; kw...)
NMRData(A::AbstractNMRData; kw...)
```

NMR配列データのための一般的な [`AbstractNMRData`](@ref) です。メモリバックされた配列を保持します。

# キーワード

  * `dims`: 配列のための `NMRDimension` の `Tuple`。
  * `name`: 配列のための `Symbol` 名。これは、`NMRData` が NetCDF のようなマルチレイヤーのファイルで使用されるときに、名前付きレイヤーを取得します。
  * `missingval`: 欠損データを表す値で、通常はファイルから検出されます。値が指定されていないか、間違っていることがわかっている場合は手動で設定します。これは NMRData の値を変更することはなく、単に欠損として扱われる値を割り当てます。

# 内部キーワード

場合によっては、これらのキーワードを設定することも可能です。

  * `data`: `AbstractNMRData` のデータを置き換えることができます。
  * `refdims`: 配列がスライスされた位置の `Dimension` の `Tuple` で、デフォルトは `()` です。
