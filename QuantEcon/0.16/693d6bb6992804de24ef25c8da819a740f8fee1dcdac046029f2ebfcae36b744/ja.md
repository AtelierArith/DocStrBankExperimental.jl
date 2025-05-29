```
k_array_rank([T=Int], a)
```

k個の異なる正の整数からなる配列`a`が昇順にソートされているとき、要素の降順の列の辞書順でのランキングを返します。これは[組合せ数システム](https://en.wikipedia.org/wiki/Combinatorial_number_system)に従います。

# 注意事項

計算中にオーバーフローが発生した場合、`InexactError`例外がスローされるか、警告なしに不正確な値が返されます。入力配列のランクが`T`の範囲内に収まることを確認するのはユーザーの責任です。そのための十分な条件は`binomial(BigInt(a[end]), BigInt(length(a))) <= typemax(T)`です。

# 引数

  * `T::Type{<:Integer}`: 返されるランキングの数値型。
  * `a::Vector{<:Integer}`: 長さkの配列。

# 戻り値

  * `idx::T`: `a`のランキング。
