```
hybridlambdaformat(net::HybridNetwork; prefix="I")
```

出力 `net` を、[Hybrid-Lambda](https://github.com/hybridLambda/hybrid-Lambda) シミュレーターが期待する形式の文字列として返します。具体的には：

  * すべての内部ノードには名前が付けられ、ルートを含めて、名前は一意であり、文字で始まります。
  * ハイブリッドノードは `H6#γ1:length1` および `H6#γ1:length2` のように書かれ、`#H6:length1::γ1` および `#H6:length2::γ2` のようには書かれません（Hybrid-Lambda が期待する同じ γ 値に注意してください）。

これは、[拡張ニューイック](https://doi.org/10.1186/1471-2105-9-532) 形式の修正版です。

オプションのキーワード引数 `prefix`：文字で始まる必要があり、「H」以外でなければなりません。内部ノードには "I1"、"I2" などの名前が付けられます。既存の内部非ハイブリッドノードの名前は**置き換えられ**、これはノード名が文字で始まらない場合（例えば、ノード名がブートストラップ値である場合）に重要です。ノード名を追加するには、[`nameinternalnodes!`](@ref) を参照してください。

# 例

```jldoctest
julia> net = readnewick("((a:1,(b:1)#H1:1::0.8):5,(#H1:0::0.2,c:1):1);");

julia> hybridlambdaformat(net) # net はここで変更されません
"((a:1.0,(b:1.0)H1#0.8:1.0)I1:5.0,(H1#0.8:0.0,c:1.0)I2:1.0)I3;"

julia> # using PhyloPlots; plot(net, shownodenumber=true) # ノード -2 がルートであることを示します

julia> rotate!(net, -2)

julia> writenewick(net) # γ=0.2 の小さなエッジが最初に表示されます
"((#H1:0.0::0.2,c:1.0):1.0,(a:1.0,(b:1.0)#H1:1.0::0.8):5.0);"

julia> hybridlambdaformat(net)
"((H1#0.2:0.0,c:1.0)I2:1.0,(a:1.0,(b:1.0)H1#0.2:1.0)I1:5.0)I3;"

julia> net = readnewick("((((B)#H1:::.6)#H2,((D,C,#H2:::0.8),(#H1,A))));"); # 2 つの網状構造、枝の長さなし

julia> writenewick(net, round=true)
"(#H2:::0.2,((D,C,((B)#H1:::0.6)#H2:::0.8),(#H1:::0.4,A)));"

julia> hybridlambdaformat(net; prefix="int")
"(H2#0.2,((D,C,((B)H1#0.6)H2#0.2)int1,(H1#0.6,A)int2)int3)int4;"
```
