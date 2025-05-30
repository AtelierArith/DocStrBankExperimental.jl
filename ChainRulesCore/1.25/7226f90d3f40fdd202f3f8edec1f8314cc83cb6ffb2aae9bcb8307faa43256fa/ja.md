```
canonicalize(tangent::Tangent{P}) -> Tangent{P}
```

プライマルタイプ `P` の標準的な `Tangent` を返します。返される `Tangent` のプロパティ名はプライマルのフィールド名と一致し、入力された `tangent` に存在しない `P` のすべてのフィールドは明示的に `ZeroTangent()` に設定されます。
