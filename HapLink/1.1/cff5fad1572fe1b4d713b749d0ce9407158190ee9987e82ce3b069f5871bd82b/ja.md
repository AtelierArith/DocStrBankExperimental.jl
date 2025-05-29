```
occurrence_matrix(
    haplotype::AbstractArray{Variation{S,T}},
    reads::AbstractArray{Haplotype{S,T}},
) where {S<:BioSequence,T<:BioSymbol}
occurrence_matrix(
    haplotype::Haplotype{S,T},
    reads::AbstractArray{S,T}
) where {S<:BioSequence,T<:BioSymbol}
```

`haplotype`内の変異が`reads`に何回現れるかを$N$次元の行列として決定します。

# 引数

  * `haplotype::AbstractArray{Variation}`: 探索するための`Variation`の`Vector`またはハプロタイプとしての`Haplotype`
  * `reads::AbstractArray{Haplotype}`: `haplotype`を検索するためのリード

# 戻り値

  * `2x2x... Array{Int, length(haplotype)}`: $N$次元の行列で、$N$は`readmatches`内の変異位置の数です。$n$次元の$1$インデックス位置は、$n$番目の変異位置がリファレンス塩基として呼ばれた回数を表し、$2$インデックス位置は、$n$番目の変異位置が代替塩基として呼ばれた回数を表します。例えば、`first(occurrence_matrix(reads))`は、`reads`内で全リファレンス塩基ハプロタイプが見つかった回数を示し、`occurrence_matrix(reads)[end]`は、全代替塩基ハプロタイプが見つかった回数を示します。

```
