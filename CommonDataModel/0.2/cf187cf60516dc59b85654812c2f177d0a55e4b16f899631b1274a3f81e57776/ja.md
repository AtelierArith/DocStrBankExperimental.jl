```
v = CommonDataModel.defVar(ds::AbstractDataset,src::AbstractVariable)
```

データセット `ds` において、変数 `src` からコピーされた変数を定義して返します。変数名、次元名、属性、およびデータは `src` からコピーされます。
