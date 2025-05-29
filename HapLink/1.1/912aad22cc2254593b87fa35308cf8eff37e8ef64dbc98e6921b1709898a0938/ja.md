```
variations_match(reference::Pseudoread, query::Union{Pseudoread,Haplotype})
```

`query`が`reference`からのリードである可能性がある場合、`true`を返します。

`reference`に存在しない`query`内の追加の`Variation`は、`Variation`が`reference`を[`contradicts`](@ref)しない限り、正の一致結果を無効にしません。これらの`Variation`は次のいずれかです。

1. `reference`の長さを超えて拡張する、または
2. `reference`の間隔内に「シーケンシングエラー」として存在する

一方で、`reference`と`query`の重複する間隔内の`Variation`は、`reference`に存在するものであれば**すべて**`query`にも見つけられなければなりません。言い換えれば、`query`は重複部分内の`reference`をすべて持っている必要がありますが、`reference`は`query`のすべてを持つ必要はありません。

この配置により、[`simulate`](@ref)を介して行われるように、一致する[`Pseudoread`](@ref)の集合体を作成することが可能になります。
