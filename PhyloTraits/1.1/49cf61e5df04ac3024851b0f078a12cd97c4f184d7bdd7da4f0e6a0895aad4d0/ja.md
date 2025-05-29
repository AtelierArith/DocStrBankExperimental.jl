```
rand([rng::AbstractRNG,]
      model::TraitSubstitutionModel,
      net::HybridNetwork;
      ntraits=1,
      keepinternal=true,
      checkpreorder=true)
```

供給された進化モデルに基づいて、根付き進化ネットワーク上で離散的な形質の進化をシミュレートします。形質のサンプリングは根で均一です。

オプションの引数:

  * `ntraits`: シミュレートする形質の数（デフォルト: 1 形質）。
  * `keepinternal`: true の場合、内部ノードを含むすべてのノードでのキャラクターステートをエクスポートします。false の場合、ティップのみでのキャラクターステートをエクスポートします。

出力:

  * 形質ごとに1行、ノードごとに1列のキャラクターステートの行列; これらのステートは `model.label` の *インデックス* であり、形質ラベルそのものではありません。
  * キャラクターステート行列の列と同じ順序でのノードラベル（ティップ用）またはノード番号（内部ノード用）のベクター

# 例

```jldoctest
julia> m1 = BinaryTraitSubstitutionModel(1.0, 2.0, ["low","high"]);

julia> net = readnewick("(((A:4.0,(B:1.0)#H1:1.1::0.9):0.5,(C:0.6,#H1:1.0::0.1):1.0):3.0,D:5.0);");

julia> using Random; Random.seed!(95);

julia> trait, lab = rand(m1, net)
([1 2 … 1 1], ["-2", "D", "-3", "-6", "C", "-4", "H1", "B", "A"])

julia> trait
1×9 Matrix{Int64}:
 1  2  1  1  2  2  1  1  1

julia> lab
9-element Vector{String}:
 "-2" 
 "D"  
 "-3" 
 "-6" 
 "C"  
 "-4" 
 "H1"
 "B"  
 "A"  
```
