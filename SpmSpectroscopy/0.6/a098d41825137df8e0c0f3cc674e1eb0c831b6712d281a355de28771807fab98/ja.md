```
load_spectrum(filename::AbstractString; select::AbstractVector=Bool[], header_only::Bool=false, remove_missing::Bool=false,
    index_column::Bool=false, index_column_type::Type=Int)::SpmSpectrum
```

ファイル `filename` からスペクトルを読み込みます。現在、Nanonis .dat ファイルのみがサポートされています。`select` を使用して読み込む列を指定できます（`select` の説明については CSV.jl を参照してください）。`header_only` が `true` の場合、ヘッダーのみが読み込まれます。`index_column` が `true` の場合、`index_column_type` 型のインデックスを持つ追加の列が追加されます。`remove_missing` が `true` の場合、欠損値は削除されます。
