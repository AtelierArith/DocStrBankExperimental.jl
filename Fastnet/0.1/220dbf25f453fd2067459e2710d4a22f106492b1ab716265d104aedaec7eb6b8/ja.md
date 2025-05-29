```
degreedist(net::FastNet)
```

ネットワークの次数分布を指定するFloat64のベクトルを返します。

返されるベクトルの要素kは、ネットワークからランダムに選ばれたノードが次数kである確率です。

ベクトルの要素が1.0に合計しない場合、残りはランダムに選ばれたノードが次数ゼロである確率です。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード0個、リンク0個のネットワーク

julia> makenodes!(net,4,1)

julia> makelink!(net,node(net,1),node(net,2));

julia> makelink!(net,node(net,2),node(net,3));

julia> degreedist(net)
2-element Vector{Float64}:
 0.5
 0.25
```
