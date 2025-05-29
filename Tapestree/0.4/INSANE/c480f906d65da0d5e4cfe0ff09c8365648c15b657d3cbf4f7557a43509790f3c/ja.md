```
sT_label
```

`insane` 用のラベル付き二分系統樹を表すスーパタイプ `sT` の複合再帰型で、以下のフィールドを持ちます：

d1: 娘木 1   d2: 娘木 2   e:  エッジ   l:  ラベル

```
sT_label()
```

空の `sT_label` オブジェクトを構築します。

```
sT_label(e::Float64)
```

エッジ `e` を持つ空の `sT_label` オブジェクトを構築します。

```
sT_label(d1::sT_label, d2::sT_label, e::Float64)
```

二つの `sT_label` 娘とエッジ `e` を持つ `sT_label` オブジェクトを構築します。
