```
eachsample(dt::AbstractDataTable)
```

各サンプルに属するデータを `Vector` として取得するイテレータを作成します。`SampleDataTable` の場合、新しいベクターが作成されます; これらのベクターを変更しても `dt` の値は変わりません。
