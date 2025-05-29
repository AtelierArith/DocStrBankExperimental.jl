```
run_unfold(dataDF, bfDict; 
	eventcolumn="event",
	remove_time_expanded_Xs=true, 
	extract_data = raw_to_data, 
	verbose::Bool=true, 
	kwargs...)
```

dataDF内のすべてのデータに対してUnfold分析を実行します。

## キーワード

  * `eventcolumn::String = "event"`  Unfoldが分析中に使用する列。
  * `remove_time_expanded_Xs::Bool = true`  メモリ消費を大幅に削減する時間拡張デザインマトリックスを削除します。このXsはほとんど必要ありませんが、回復可能です（Unfold.load関数を参照してください）。
  * `extract_data::function = raw_to_data`  MNE Rawオブジェクトをデータ配列に変換する関数を指定します。デフォルトは`raw_to_data`で、`get_data`を使用し、`channels`を選択することができます - @Ref(`raw_to_data`)を参照してください。オプションのkw-引数（例：channels）は、`run_unfold`関数内でkw-引数として直接指定する必要があります。
  * `verbose::Bool = true)`  プログレスバーを表示するかどうか。
