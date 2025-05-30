```
AbstractDiffEqArray{T, N, A} <: AbstractVectorOfArray{T, N, A}
```

時間配列 `A.t` の追加情報を持つ AbstractVectorOfArray オブジェクトで、時間系列を指定します。標準的な AbstractDiffEqArray の例は、`DiffEqArray([[1,2],[3,4]],[1.0,2.0])` のペアリングで、これは時間 1.0 での値が `[1,2]` であり、時間 2.0 での値が `[3,4]` であることを意味します。

AbstractDiffEqArray は、追加のプロパティを持つ AbstractVectorOfArray と同じ動作をすべて持っています。

## フィールド

AbstractDiffEqArray は以下のフィールドを追加します：

  * `t` は各タイムステップの時間を保持します。
