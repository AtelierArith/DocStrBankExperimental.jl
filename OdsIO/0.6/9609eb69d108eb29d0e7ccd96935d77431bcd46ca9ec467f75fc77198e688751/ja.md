```
ods_readall(filename_or_stream; <キーワード引数>)
```

元のOpenDocument Spreadsheet（.ods）ファイルまたはストリーム内の位置または名前でインデックス付けされたテーブル|辞書|データフレームの辞書を返します。

# 引数

  * `fileaname_or_stream`: `Vector{UInt8}`としてのファイル名またはストリーム
  * `sheetsNames=[]`: データをインポートするシート名のリスト。
  * `sheetsPos=[]`: データをインポートするシートの位置のリスト（1から始まる）。
  * `ranges=[]`: 各シートからデータをインポートする範囲を定義するタプルのペアのリスト、形式は((tlr,tlc),(brr,brc))
  * `innerType="Matrix"`: 返される内部コンテナのタイプ。"Matrix"、"Dict"、または"DataFrame"のいずれか。

# 注意事項

  * sheetsNamesとsheetsPosは同時に指定できません
  * rangesは行と列の両方に対して整数位置を使用して定義されます
  * 個々の辞書またはデータフレームは、範囲で指定された最初の行のセルの値、または`range`が指定されていない場合は最初の行の値でキー付けされます
  * innerType="Matrix"は、innerType="Dict"とは異なり、元の列の順序を保持し、より高速でメモリを少なく消費します
  * innerType="DataFrame"を使用すると、元の列の順序も保持され、列の型を自動的に変換しようとします（Int64、Float64、Stringの順で動作します）

# 例

```julia
julia> outDic  = ods_readall("spreadsheet.ods";sheetsPos=[1,3],ranges=[((1,1),(3,3)),((2,2),(6,4))], innerType="Dict")
Dict{Any,Any} with 2 entries:
  3 => Dict{Any,Any}(Pair{Any,Any}("c",Any[33.0,43.0,53.0,63.0]),Pair{Any,Any}("b",Any[32.0,42.0,52.0,62.0]),Pair{Any,Any}("d",Any[34.0,44.0,54.…
  1 => Dict{Any,Any}(Pair{Any,Any}("c",Any[23.0,33.0]),Pair{Any,Any}("b",Any[22.0,32.0]),Pair{Any,Any}("a",Any[21.0,31.0]))
julia> data = @pipe HTTP.get("https://github.com/sylvaticus/OdsIO.jl/raw/master/test/spreadsheet.ods").body |> ods_readall(_)
Dict{Any, Any} with 3 entries:
  "Sheet1" => Any["h1" "h2" "h3"; "a" "b" "c"; "aa" "bb" "cc"]
  "Sheet2" => Any["a" "b" "c"; 21 22 23; 31 32 33]
  "Sheet3" => Any[nothing nothing nothing nothing; nothing "b" "c" "d"; … ; nothing 52 53 54; nothing 62 63 64]
```
