GroupedArray{T,N} <: AbstractArray{T,N} N次元の密な配列で、要素の型はTであり、T <: Union{Int, Missing}です。

GroupedArrayには、次の契約を満たすフィールドngroupsがあります。

  * 構築直後、GroupedArray内の非欠損要素の集合は1:ngroupsに等しいです。
  * その後（つまり、`setindex!`を使用した後）、非欠損要素は常に1とngroupsの間に留まります。
