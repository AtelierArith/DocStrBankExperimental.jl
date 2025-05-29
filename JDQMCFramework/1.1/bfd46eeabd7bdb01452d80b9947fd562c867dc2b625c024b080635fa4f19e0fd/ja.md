```
SymPropagators
```

すべての対称伝播子タイプの統合であり、伝播子タイプが対称であるかどうかをテストするのに役立ちます。`typeof{B} <: AbstractPropagator` が `true` を返す場合、`typeof(B) <: SymPropagators` が `true` を返すとき、`B` は対称伝播子を表し、そうでなければ非対称伝播子を表します。
