```
sample_gumbel_softmax(; probs = nothing, logits = nothing, tau = 0.1, hard = true, epsilon = 1e-10)
```

Gumbel-Softmax分布からサンプリングします。Gumbel-Softmax分布は、カテゴリカル分布の連続的な緩和です。次のように定義されます：

```
Gumbel-Softmax(logits) = softmax((logits + Gumbel(0, 1)) / tau)
```

ここで、tauは分布の滑らかさを制御する温度パラメータです。期待される入力は`probs`または`logits`のいずれかです。`logits`が提供されていない場合、`log(probs + epsilon)`として計算されます。ここで、`epsilon`は数値的不安定性を避けるための小さな値です。`logits`の期待される形状は、Fluxと一貫性を保つために`(latent_dimension, categorial_dimension, batch_dimension)`です。例えば

```julia
logits = randn(30, 10, 64) # ここでは64バッチをサンプリングしています。各バッチには10クラスの30のカテゴリカル分布があります。
z = sample_gumbel_softmax(logits=logits, tau=0.5)
sizeof(z) # (30, 10, 64)
```

結果は、`hard`が`true`に設定されている場合はワンホットエンコードされます。`hard`が`false`に設定されている場合、結果はSoftmaxのソフト出力になります。
