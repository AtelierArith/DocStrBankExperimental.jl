```
timedata_operation(f::Function, x, y)
```

`f`を要素ごとに、潜在的に`TimeSeries`、`TimePattern`、または``Map`引数`x`と`y`に対して実行します。

`x`と`y`の両方が`TimeSeries`または`TimePattern`である場合、`x`と`y`のタイムスタンプが結合され、両方の時間依存データが各タイムスタンプでサンプリングされて、所望の操作が実行されます。`ts1`または`ts2`のいずれかが`TimeSeries`である場合、`TimeSeries`が返されます。`ts1`または`ts2`のいずれかに`ignore_year`または`repeat`フラグが`true`に設定されている場合、結果の`TimeSeries`もそうなります。`Map`の場合、非マップオペランドが見つかるまで再帰を実行します。

注意！現在、`Map-Map`操作は`Map`インデックスが同一である必要があります！ ```
