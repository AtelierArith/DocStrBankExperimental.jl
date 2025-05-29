```
NetworkNodeWithRetrofit <:NetworkNode
```

CO₂キャプチャをノードにレトロフィットすることを許可するための抽象スーパタイプです。その適用には、ユーザーが以下を行う必要があります。

1. 自分のノードを `NetworkNodeWithRetrofit` のサブタイプとして定義すること。
2. 上記のノードに `co2_proxy` フィールドを含めるか、またはノードのための `co2_proxy` メソッドを定義すること。

このアプリケーションは、[`RefNetworkNodeRetrofit`](@ref) によって最もよく説明されており、[`RefNetworkNode`](@extref EnergyModelsBase.RefNetworkNode) ノードに対してそれを示しています。
