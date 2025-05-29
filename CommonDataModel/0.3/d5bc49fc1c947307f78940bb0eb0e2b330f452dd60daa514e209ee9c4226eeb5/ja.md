```
v = CommonDataModel.defVar(ds::AbstractDataset,src::AbstractVariable)
v = CommonDataModel.defVar(ds::AbstractDataset,name::SymbolOrString,src::AbstractVariable)
```

データセット `ds` において、変数 `src` からコピーされた変数を定義して返します。次元名、属性、およびデータは `src` からコピーされ、変数名も `name` が提供されていない限りコピーされます。
