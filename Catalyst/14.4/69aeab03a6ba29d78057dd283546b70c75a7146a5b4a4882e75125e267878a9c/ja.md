```
@reaction_network
```

化学反応ネットワークをエンコードする[`ReactionSystem`](@ref dsl_description)を生成します。

マクロのパラメータの詳細については、[The Reaction DSL](@ref dsl_description)のドキュメントを参照してください。

例:

```julia
# 名前SIRの基本的なSIRモデル
sir_model = @reaction_network SIR begin
    c1, s + i --> 2i
    c2, i --> r
end

# ランダムに生成された名前の基本的なSIRモデル
sir_model = @reaction_network begin
    c1, s + i --> 2i
    c2, i --> r
end

# 名前emptyの空のネットワーク
emptyrn = @reaction_network empty

# ランダムに生成された名前の空のネットワーク
emptyrn = @reaction_network
```

`@reaction_network`を通じて生成されたReactionSystemsは完全です。
