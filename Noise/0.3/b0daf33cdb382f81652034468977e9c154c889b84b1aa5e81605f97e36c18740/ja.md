```
add_gauss_chn(X; clip=false[, σ=0.1, μ=0.0])
```

RGB画像`X`にガウスノイズ（標準偏差`σ`と平均`μ`）をピクセル単位で追加します。ただし、1つのピクセルのすべてのチャネルは同じ量のノイズを受け取ります。したがって、ノイズはおおむね強度 - しかし色 - を変化させるノイズとして作用します。キーワード引数`clip`が提供されると、値は[0, 1]の範囲にクリップされます。`σ`と`μ`はガウスの標準偏差と平均を表すオプションの引数です。

もし`X<:Complex`の場合、`μ`と`σ`は実部と同様に虚部に適用されます。実部と虚部で異なる動作を持たせたい場合は、単に`μ`または`σ`を複素数に選択してください。
