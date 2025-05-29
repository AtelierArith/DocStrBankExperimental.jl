```
apply_and!(inds::BitVector, d, by::Pair)
apply_and!(inds::BitVector, d, bys::Pair...)
```

指定された列に対して、`Tables.jl`互換のテーブル`d`に要素ごとに`true`または`false`を返す関数を適用し、返された配列とのビット単位の`and`を通じて`inds`の要素を更新します。関数の代わりに配列が提供された場合、列と配列の間で要素ごとの等価性（`==`）比較が適用されます。詳細は[`apply_and`](@ref)を参照してください。

関数の指定方法は、[`apply`](@ref)と同様です。複数の`Pair`が提供された場合、返された配列ごとに`inds`がビット単位の`and`を通じて更新されます。
