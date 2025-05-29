```
linkexists(net,kid)
linkexists_f(net,kid)
```

ノードID *kid* が *net* に存在する場合は true を返し、そうでない場合は false を返します。  

この関数は定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。 

また、[makelink!](#Fastnet.makelink!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
ノード数0、リンク数0のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> linkexists(net,7)
false

julia> k=makelink!(net,n1,n2);

julia> linkexists(net,k)
true
```
