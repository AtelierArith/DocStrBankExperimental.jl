```
BACON(in_dims::Int, out_dims::Int, N::Int, period::Real; hidden_dims::Int, num_layers::Int)
```

バンド制限座標ネットワーク（BACON）[lindell2021bacon](@cite)から。[`FourierFilterNet`](@ref)に似ていますが、周波数は離散的で非訓練可能です。

ヒント：パフォーマンスを向上させるために、`period`を`1,2,π`または`2π`に設定することをお勧めします。
