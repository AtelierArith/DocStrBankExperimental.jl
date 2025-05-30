```
prefixes(x::IndexEntry)
```

チェックポイント出力ファイルのプレフィックスです。これは指定された任意のプレフィックスのタプルです。チェックポイントが `checkpoint(Forecasters, "forecasts", ...)` を使用して保存された場合、その `prefixes` は `("Forecasters",)` です。一般的に実際には、チェックポイントが宣言されたモジュールに一致するものが1つあるか（前の例のように）、指定されていない場合は0です（`checkpoint("forecasts",...)` のように）。もし `checkpoint("Foo.Bar", "forecasts.jlso")` として保存された場合、プレフィックスは `("Foo", "Bar")` を返します。
