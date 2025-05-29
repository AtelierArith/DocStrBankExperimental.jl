```
write_gsheet(data::DataFrame, spreadsheet_id::String; sheet::String="Sheet1", range::String="", missing_value::String = "", append::Bool = true)
```

指定されたGoogle SheetsスプレッドシートにDataFrameの内容を書き込みます。

# 引数

  * `data::DataFrame`: Google Sheetsに書き込むデータを含むDataFrame。
  * `spreadsheet_id::String`: Google SheetsスプレッドシートのIDまたはIDを含む完全なURL。
  * `sheet::String`: データが書き込まれるスプレッドシート内のシートの名前。デフォルトは「Sheet1」。
  * `range::String`: データが書き込まれるシート内の範囲。空の場合、デフォルトは「A1」。
  * `missing_value::String`: DataFrame内の欠損エントリを置き換える値。デフォルトは空の文字列。
  * `append::Bool`: trueの場合、シート内の既存のデータにデータを追加します。falseの場合、既存のデータを上書きします。デフォルトはtrue。

# 例

```
julia> df = DataFrame(A=1:5, B=["a", missing, "c", "d", "e"], C=[1.1, 2.2, 3.3, 4.4, 5.5]);

julia> write_gsheet(df, full, sheet = "sheet2", append = false)
```
