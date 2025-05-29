```
SizeMax{K} <: AbstractProperty
SizeMax(k::Int)
```

最大-K集合のサイズ。例えば、[`IndependentSet`](@ref)問題の最大サイズは独立数としても知られています。

  * 対応するテンソル要素の型は、`K`が`Single`の場合は最大プラス熱帯数[`Tropical`](@ref)であり、`K`が整数の場合は[`ExtendedTropical`](@ref)です。
  * 重み付き制約充足問題と互換性があります。
  * BLAS（CPU上）およびGPUは、`K`が`Single`の場合にのみサポートされています。
