```
@datarun [proj] func(args...)
```

リスト `args` から名前付き `DataSet` を使って `func` を実行します。

# 例

Data.toml で定義された a,b という名前の `DataSet` をロードし、`f()` に渡します。

```
proj = DataSets.load_project("Data.toml")
@datarun proj f("a", "b")
```
