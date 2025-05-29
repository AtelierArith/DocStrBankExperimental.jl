```
ods_read(filename_or_stream; <キーワード引数>)
```

OpenDocument Spreadsheet (.ods) ファイルまたはストリーム内のシート（またはシート内の範囲）からテーブル|辞書|データフレームを返します。

# 引数

  * `fileaname_or_stream`: ファイル名または `Vector{UInt8}` としてのストリーム
  * `sheetName=nothing`: データをインポートするシート名。
  * `sheetPos=nothing`: データをインポートするシートの位置（1から始まる）。
  * `range=nothing`: データをインポートするシート内の範囲を定義するタプルのペア、形式は ((tlr,tlc),(brr,brc))
  * `retType="Matrix"`: 返されるコンテナのタイプ。"Matrix"、"Dict"、または "DataFrame" のいずれか。

# 注意事項

  * sheetName と sheetPos は同時に指定できません。
  * sheetName と sheetPos の両方が指定されていない場合、最初のシートからデータが返されます。
  * ranges は行と列の両方の整数位置を使用して定義されます。
  * 辞書またはデータフレームは、範囲で指定された最初の行のセルの値、または `range` が指定されていない場合は最初の行によってキー付けされます。
  * retType="Matrix" は、innerType="Dict" と異なり、元の列の順序を保持し、より高速でメモリを少なく消費します。
  * innerType="DataFrame" を使用すると、元の列の順序も保持され、列の型を自動的に変換しようとします（Int64、Float64、String の順で動作します）。

# 例

```julia
julia> df = ods_read("spreadsheet.ods";sheetName="Sheet2",retType="DataFrame")
3×3 DataFrames.DataFrame
│ Row │ x1   │ x2   │ x3   │
├─────┼──────┼──────┼──────┤
│ 1   │ "a"  │ "b"  │ "c"  │
│ 2   │ 21.0 │ 22.0 │ 23.0 │
│ 3   │ 31.0 │ 32.0 │ 33.0 │
julia> data = @pipe HTTP.get("https://github.com/sylvaticus/OdsIO.jl/raw/master/test/spreadsheet.ods").body |> ods_read(_)
3×3 Matrix{Any}:
 "h1"  "h2"  "h3"
 "a"   "b"   "c"
 "aa"  "bb"  "cc"
```
