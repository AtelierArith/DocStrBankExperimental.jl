```
transmission_loss(pm, tx, rxs)
```

送信元 `tx` から受信機 `rxs` への伝送損失を伝播モデル `pm` を使用して計算します。`rxs` が単一の受信機を示す場合、結果はスカラーです。`rxs` が `AbstractArray` の場合、結果は `rxs` と同じ形状の伝送損失の配列（dB単位）になります。
