```
collect_indexed_values(d)
```

インデックスを値にマッピングするDictからの解析された値（TimeSeries、TimePattern、Mapなど）。

## 例

```
@assert collect_indexed_values(indexed_values(ts)) == ts
```
