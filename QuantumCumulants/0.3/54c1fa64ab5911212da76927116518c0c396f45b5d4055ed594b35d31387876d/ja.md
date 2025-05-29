```
IndexedAverageDoubleSum <: CNumber
```

[`IndexedAverageSum`](@ref) に対する記号的な総和を定義し、[`Index`](@ref) エンティティを使用します。これは、平均の積に対する二重和を概念的に表現します。

# フィールド:

  * innerSum: [`IndexedAverageSum`](@ref) エンティティ。
  * sum_index: （外側の）総和が行われるインデックス。
  * non*equal*indices: （オプション）外側の総和インデックスと等しくなってはいけないインデックスのベクトル。
