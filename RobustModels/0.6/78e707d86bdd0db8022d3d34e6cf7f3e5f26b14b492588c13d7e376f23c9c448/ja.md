```
leverage(m::RobustLinearModel, variant::Symbol)
```

モデルの`leverage`を異なる重みベクトルを使用して返します。バリアントに応じて:     - `variant = :original`: ユーザー定義の重みを使用します。重みが使用されていない場合（重みベクトルのサイズが0の場合）、重みは使用されません。     - `variant = :fitted`: IRLS手法からの適合モデルの作業重みを使用します。
