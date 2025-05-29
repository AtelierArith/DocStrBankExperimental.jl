```
array_of_ranges = kfoldperm(N, k; breaks=[])
```

1から`N`までのインデックスのリストを`k`グループに分割します。

# 引数

  * `N`: (`::Integer`) 整理する要素の数
  * `k`: (`::Integer`) `N`要素を分割するグループの数。

# キーワード

  * `breaks`: (`::Vector{<:Integer}`, `=[]`) 事前に定義されたブレークポイントが配置されるインデックスの配列。

# 戻り値

  * `array_of_ranges`: (`::Vector{UnitRange{<:Integer}}`) 異なるグループの範囲を含む配列。目標は`k`グループですが、`breaks`入力配列に要素を追加することで増加する可能性があります。
