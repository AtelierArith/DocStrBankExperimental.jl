```
write_dataframes(resultfolder::String, datapath::String; measure::Symbol=:AIC, assemble::Bool=true, fittedparams=Int[])
```

write_dataframes(resultfolder::String,datapath::String;measure::Symbol=:AIC,assemble::Bool=true)

実行結果をcsvファイルにまとめます

引数

  * `resultfolder`: 結果ファイルがあるフォルダの名前
  * `datapath`: データが保存されているフォルダの名前
  * `measure`: 勝者を評価するために使用される測定値
  * `assemble`: trueの場合、結果を要約ファイルにまとめます
