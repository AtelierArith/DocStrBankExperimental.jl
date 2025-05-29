```
dice_coeff_loss(ŷ, y; smooth = 1)
```

ダイス係数に基づく損失を返します。[V-Net](https://arxiv.org/abs/1606.04797) 画像セグメンテーションアーキテクチャで使用されます。ダイス係数はF1スコアに似ています。損失は次のように計算されます：

```
1 - 2*sum(|ŷ .* y| + smooth) / (sum(ŷ.^2) + sum(y.^2) + smooth)
```

# 例

```jldoctest
julia> y_pred = [1.1, 2.1, 3.1];

julia> Flux.dice_coeff_loss(y_pred, 1:3)
0.000992391663909964

julia> 1 - Flux.dice_coeff_loss(y_pred, 1:3)  # ~ 画像セグメンテーションのF1スコア
0.99900760833609
```
