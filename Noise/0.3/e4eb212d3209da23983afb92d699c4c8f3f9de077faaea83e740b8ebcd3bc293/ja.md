```
mult_gauss_chn(X; clip=false[, σ=0.1, μ=0.0])
```

RGB画像`X`を返し、ピクセルの値がガウス分布（標準偏差`σ`と平均`μ`）でピクセルごとに乗算されます。ただし、1つのピクセルのすべてのチャネルは同じ量のノイズを受け取ります。したがって、ノイズはおおよそ強度を変えるノイズとして作用しますが、色は変わりません。キーワード引数`clip`が提供されると、値は[0, 1]の範囲にクリップされます。`σ`と`μ`はガウスの標準偏差と平均を表すオプションの引数です。

もし`X<:Complex`の場合、`μ`と`σ`は実部と同様に虚部にも適用されます。実部と虚部で異なる動作を持たせたい場合は、単に`μ`または`σ`を複素数に選択してください。
