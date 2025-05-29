```
function external_vertex(ops::OperatorProduct;
    name="", factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

与えられた OperatorProduct `ops` から、純粋な外部頂点のためのいくつかの量子演算子を含む ExternalVertex 型の FeynmanGraph を作成します。
