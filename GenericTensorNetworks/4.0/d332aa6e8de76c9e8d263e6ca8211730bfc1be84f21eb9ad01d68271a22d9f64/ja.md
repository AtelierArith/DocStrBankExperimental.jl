```
SizeMin{K} <: AbstractProperty
SizeMin(k::Int)
```

最小-Kセットサイズ。例えば、[`MaximalIS`](@ref)問題の最小サイズは独立支配数としても知られています。

  * 対応するテンソル要素の型は、`K`が`Single`の場合は反転した最大プラス熱帯数[`Tropical`](@ref)であり、`K`が整数の場合は反転した[`ExtendedTropical`](@ref)です。

反転した熱帯数は、最小プラス熱帯数を模倣します。

  * 重み付き制約充足問題と互換性があります。
  * BLAS（CPU上）およびGPUは、`K`が`Single`の場合のみサポートされています。
