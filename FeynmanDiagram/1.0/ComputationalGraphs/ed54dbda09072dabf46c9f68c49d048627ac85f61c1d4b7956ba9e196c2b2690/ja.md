```
function interaction(ops::OperatorProduct; name="", reorder::Union{Function,Nothing}=nothing,
    factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

与えられた OperatorProduct `ops` から Interaction 型の FeynmanGraph を作成し、頂点のためにいくつかの量子演算子を含めます。演算子の順序付けのために reorder 関数を呼び出すことができます。  
