```
TargetNetwork(network::FluxApproximator; sync_freq::Int = 1, ρ::Float32 = 0f0)
```

FluxApproximatorをラップして、近似器のモデルに向かって更新されるターゲットネットワークを保持します。

  * `sync_freq`は、`target`の各更新間の`network`の更新回数です。
  * ρ (ホ) は「更新時にターゲットのどれだけを保持するか」です。

TargetNetworkの一般的な2つの使用法は次のとおりです。

  * ρ = 0を使用して、sync_freqごとに`target`を`network`で完全に置き換えます。
  * ρ < 1（ただし1に近い）およびsync_freq = 1を使用して、ポリャック平均を用いてターゲットが`network`に従うようにします。

`RLBase.optimise!(::TargetNetwork, ::Gradient)`インターフェースを実装して、勾配でモデルを更新し、重みの置き換えまたはポリャック平均でターゲットを更新します。

開発者への注意: `model(::TargetNetwork)`はトレーニング可能なFluxモデルを返し、`target(::TargetNetwork)`はターゲットモデルを返し、`target(::FluxApproximator)`はトレーニング不可能なFluxモデルを返します。RLCoreのドキュメントを参照してください。
