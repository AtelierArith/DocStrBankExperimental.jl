```
getsample(dt::AnalyteDataTable, id::Int)
getsample(dt::SampleDataTable, id::Int)
getsample(dt::AnalyteDataTable, sample)
getsample(dt::SampleDataTable, sample)
```

`samples`または`sampleobj(dt)[id]`に属するデータを`Vector`として取得します。`SampleDataTable`の場合、新しいベクターが作成されます。このベクターを変更しても`dt`の値は変わりません。
