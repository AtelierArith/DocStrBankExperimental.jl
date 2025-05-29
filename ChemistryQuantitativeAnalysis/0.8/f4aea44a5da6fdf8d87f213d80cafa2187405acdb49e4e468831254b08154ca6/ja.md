```
eachanalyte(dt::AbstractDataTable)
```

各分析物に属するデータを `Vector` として取得するイテレータを作成します。`AnalyteDataTable` の場合、新しいベクターが作成されます; これらのベクターを変更しても `dt` の値は変わりません。
