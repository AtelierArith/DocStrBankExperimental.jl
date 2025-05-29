```
PolymerSystem{T} <: AbstractSystem
```

`χN_map`のキーは2要素の`Set`であるべきです。各要素は種のユニークなシンボルです。例えば、AB二ブロックコポリマーの`χN_map`は、1つのエントリ`Set([:A, :B]) => χN`を持つ`Dict`です。

注意: エドワーズモデルA（ホモポリマー + 暗黙の溶媒）では、関数`multicomponent`が正しい結果を返すように、`components`配列にダミーの溶媒成分を追加する必要があります。
