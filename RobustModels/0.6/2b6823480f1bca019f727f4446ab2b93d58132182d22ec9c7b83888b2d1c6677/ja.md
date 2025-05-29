```
vcov(m::RobustLinearModel, variant::Symbol)
```

モデルの `vcov` を異なる重みベクトルを使用して返します。バリアントに応じて:     - `variant = :original`: ユーザー定義の重みを使用します。重みが使用されていない場合（重みベクトルのサイズが 0 の場合）、重みは使用されません。     - `variant = :fitted`: IRLS 手法からの適合モデルの作業重みを使用します。
