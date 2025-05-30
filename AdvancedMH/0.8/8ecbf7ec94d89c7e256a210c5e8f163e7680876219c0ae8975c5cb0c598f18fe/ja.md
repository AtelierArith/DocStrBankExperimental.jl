```
MetropolisHastings{D}
```

`MetropolisHastings` には 1 つのフィールド `proposal` があります。 `proposal` は `Proposal`、`NamedTuple` の `Proposal`、またはデータの形状に合わせた `Array{Proposal}` です。たとえば、サンプラーが次の形状の `NamedTuple` を返すようにしたい場合

```julia
x = (a = 1.0, b=3.8)
```

提案は次のようになります。

```julia
proposal = (a=StaticProposal(Normal(0,1)), b=StaticProposal(Normal(0,1)))
```

他に許可されている提案は次のとおりです。

```
p1 = StaticProposal(Normal(0,1))
p2 = StaticProposal([Normal(0,1), InverseGamma(2,3)])
p3 = StaticProposal((a=Normal(0,1), b=InverseGamma(2,3)))
p4 = StaticProposal((x=1.0) -> Normal(x, 1))
```

サンプラーは次のように構築されます。

```julia
spl = MetropolisHastings(proposal)
```

`sample` 関数を使用して `MetropolisHastings` を使用する場合、次のキーワード引数が許可されます。

  * `initial_params` はモデルの初期パラメータ化を定義します。もし

何も指定されていない場合、初期パラメータはサンプラーの提案から引き出されます。

  * `param_names` はパラメータに割り当てられる文字列のベクターです。これは

`chain_type=Chains` の場合にのみ使用されます。

  * `chain_type` は返されるチェーンのタイプです。サポートされている

タイプは、`MCMCChains` がインポートされている場合は `chain_type=Chains`、または `StructArrays` がインポートされている場合は `chain_type=StructArray` です。
