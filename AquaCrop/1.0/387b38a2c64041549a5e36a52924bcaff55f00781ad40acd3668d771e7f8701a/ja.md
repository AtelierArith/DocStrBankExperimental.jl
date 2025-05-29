```
write_out_csv(file, cropfield::AquaCropField, field::Symbol; kwargs...)
```

`cropfield.outputs[field]` のデータフレームを `file` に csv 形式で書き込みます。

これは `CSV.write` のラッパーで、単位を削除します。キーワード引数 `kwargs` は `CSV.write` に渡されます。

`digits` キーワード引数が提供されている場合、指定された小数点以下の桁数に丸められます。そうでない場合は、デフォルトの `digits=4` が使用されます。
