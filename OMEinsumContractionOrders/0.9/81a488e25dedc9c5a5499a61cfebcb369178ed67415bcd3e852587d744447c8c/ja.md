```
contraction_complexity(eincode, size_dict) -> ContractionComplexity
```

einsum収束の時間、空間、読み書きの複雑さを返します。返されるオブジェクトには3つのフィールドが含まれています：

  * 時間の複雑さ `tc` は `log2(要素ごとの乗算の数)` と定義されます。
  * 空間の複雑さ `sc` は `log2(最大中間テンソルのサイズ)` と定義されます。
  * 読み書きの複雑さ `rwc` は `log2(読み書き操作の数)` と定義されます。
