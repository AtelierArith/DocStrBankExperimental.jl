```
Coerce(col₁ => S₁, col₂ => S₂, ..., colₙ => Sₙ)
```

新しい仕様に合わせて、列の科学的型が一致するようにテーブルのコピーを返します。

```
Coerce(S)
```

科学的型 `S` を持つテーブルのすべての列を強制します。

この変換は `DataScienceTraits.coerce` 関数を使用します。詳細については、ドキュメント文字列を参照してください。

# 例

```julia
using DataScienceTraits
Coerce(1 => Continuous, 2 => Continuous)
Coerce(:a => Continuous, :b => Continuous)
Coerce("a" => Continuous, "b" => Continuous)
```
