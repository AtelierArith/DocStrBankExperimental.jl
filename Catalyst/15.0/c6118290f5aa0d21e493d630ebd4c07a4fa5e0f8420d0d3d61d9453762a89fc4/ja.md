```
@reaction_network
```

化学反応ネットワークモデル（Catalyst `ReactionSystem`）を生成するためのマクロ。マクロが実装するドメイン固有言語（DSL）に関する詳細は、Catalystドキュメントの（[DSLの紹介](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_basics/)および[利点の使用](https://docs.sciml.ai/Catalyst/stable/model_creation/dsl_advanced/)）のセクションを参照してください。マクロの出力（`ReactionSystem`構造体）は、Catalystおよびその機能の中心です。これらをシミュレートする方法については、[Catalystドキュメント](https://docs.sciml.ai/Catalyst/stable/)に記載されています。

返すもの:

  * Catalyst `ReactionSystem`、すなわち反応ネットワークのための象徴的モデル。返される

システムは`complete`としてマークされています。例えば、合成モデリングに使用するために完全でない`ReactionSystem`を取得するには、同様の`@network_component`マクロを参照してください。

例: ここでは基本的なSIRモデルを作成します。これは2つの反応（感染と回復）を含みます：

```julia
sir_model = @reaction_network begin
    c1, S + I --> 2I
    c2, I --> R
end
```

次に、自己活性化ループを作成します。ここでは、単一のコンポーネント（`X`）がミカエリス・メンテン関数を用いて自らの生成を活性化します：

```julia
sa_loop = @reaction_network begin
    mm(X,v,K), 0 --> X
    d, X --> 0
end
```

このモデルには、生成および分解反応も含まれており、`0`は反応に基質または生成物が存在しないことを示します。

オプション: 反応に加えて、マクロは「オプション」入力もサポートしています（例えば、観測可能なものの追加を許可します）。各オプションは、`@`で始まるタグとその入力で指定されます。オプションのリストは[こちら](https://docs.sciml.ai/Catalyst/stable/api/#api_dsl_options)で見つけることができます。
