```
sTf_label
```

スーパタイプ `sT` の合成再帰型で、化石を持つラベル付き二分系統樹を `insane` 用に表現し、以下のフィールドを持ちます：

d1: 娘木 1   d2: 娘木 2   e: エッジ   iμ: 絶滅しているかどうか   iψ: 化石であるかどうか   l: ラベル

```
sTf_label(e::Float64, iμ::Bool, iψ::Bool, l::String)
```

エッジ `e` とラベル `l` を持つ空の `sTf_label` オブジェクトを構築します。

```
sTf_label(d1::sTf_label e::Float64, l::String)
```

1 つの `sTf_label` 娘とエッジ `e` を持つ `sTf_label` オブジェクトを構築します。

```
sTf_label(d1::sTf_label, d2::sTf_label, e::Float64, l ::String)
```

2 つの `sTf_label` 娉とエッジ `e` を持つ `sTf_label` オブジェクトを構築します。
