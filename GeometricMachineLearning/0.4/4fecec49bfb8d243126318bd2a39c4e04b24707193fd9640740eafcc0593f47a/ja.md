```
TransformerIntegrator <: Architecture
```

さまざまなトランスフォーマーアーキテクチャを包含しており、例えば[`VolumePreservingTransformer`](@ref)や[`LinearSymplecticTransformer`](@ref)などがあります。

この背後にある中心的なアイデアは、明示的なマルチステップインテグレーターを構築することです：

$$
    \mathtt{Integrator}: [ z^{(t - \mathtt{sl} + 1)}, z^{(t - \mathtt{sl} + 2)}, \ldots, z^{(t)} ] \mapsto [ z^{(t + 1)}, z^{(t + 2)}, \ldots, z^{(t + \mathtt{pw})} ],
$$

ここで、`sl`は*シーケンスの長さ*を、`pw`は*予測ウィンドウ*を表し、それぞれ入力ベクトルと出力ベクトルの数を示します。
