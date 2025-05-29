```
exportplan(plan; options)
exportplan(file, plan; options)
```

プランを表示するか、テキストファイルに保存します。

### オプション

  * `alphabetical=false` - 変数をソートするには `true` に設定します。デフォルトでは、変数はモデルと同じ順序でリストされます。
  * `exog_mark="X"` - 外生的値をマークするための短い文字列（理想的には1文字）。
  * `endo_mark="-"` - 内生的値をマークするための短い文字列（理想的には1文字）。
  * `delim=" "` - デリミタ。CSVファイルにするには `","` を使用します。

[`importplan`](@ref) も参照してください。
