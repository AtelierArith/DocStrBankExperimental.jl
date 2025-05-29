```
sample_rao_gumbel_softmax(; probs=nothing, logits=nothing, k=1, tau=1.0, I=nothing, epsilon=1e-10)
```

Rao-Blackwellized Gumbel-Softmax分布からサンプリングします。詳細についてはhttps://arxiv.org/abs/2010.04838を参照してください。期待される入力は`probs`または`logits`のいずれかです。`logits`が提供されていない場合、`log(probs + epsilon)`として計算されます。ここで、`epsilon`は数値的不安定性を避けるための小さな値です。`logits`の期待される形状は`(latent_dimension, categorial_dimension, batch_dimension)`で、Fluxと一貫性を保ちます。`tau`は分布の滑らかさを制御する温度パラメータです。`k`はモンテカルロサンプルの数です。
