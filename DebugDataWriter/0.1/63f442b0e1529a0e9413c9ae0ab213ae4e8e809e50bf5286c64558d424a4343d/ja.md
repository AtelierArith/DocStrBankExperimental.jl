```
@debug_output debug_id title data_or_func fmt
```

[`@debug_output`](@ref)と同様に、`debug_id`、`title`、`data_or_func`引数を持ちます。追加の`fmt`引数は出力形式を指定します。デフォルトはJSONです。実装されている形式は、JSON.jlによるJSON、PrettyTables.jlによるHTMLおよびTXT、そして生データ出力としてのSVG、XMLです。

`FORMAT_WRITERS`辞書の詳細を参照してください。
