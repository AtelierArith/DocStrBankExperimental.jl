```
makenodes!(net,N,s)
makenodes_f!(net,N,s)
```

ネットワーク *net* に状態 *s* の *N* ノードを作成します。  

この関数の最悪のパフォーマンスは、ノードの状態の数にのみスケールします。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [basic concepts](concepts.md) を参照してください。 

また、[makenode!](#Fastnet.makenode!)、[destroynode!](#Fastnet.destroynode!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,100,1);

julia> net
Network of 100 nodes and 0 links
```
