```
sino = fbp_sino_filter(sino::Array, filter::Vector ; extra=0)
```

2D FBP画像再構成のために、シノグラムにラプのようなフィルターを適用します。2Dおよび3Dの平行ビームおよびファンビームトモグラフィー幾何学の両方をサポートしています。

# 入力

  * `sino::AbstractArray{<:Number}` `[nb (L)]` シノグラム
  * `filter::AbstractVector` `(npad ≥ nb)` アポダイズされたラプフィルター周波数応答

# オプション

  * `extra::Int` 追加のシノグラム放射サンプルの数を保持する (デフォルト: 0)
  * `npad::Int` パディングされたサンプルの数 (デフォルト: 次の2の累乗)

# 出力

  * `sino::AbstractArray` フィルタリングされた行を持つシノグラム
