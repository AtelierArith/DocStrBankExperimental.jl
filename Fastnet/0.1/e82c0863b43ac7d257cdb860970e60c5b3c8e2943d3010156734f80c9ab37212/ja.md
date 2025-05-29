```
randomnode(net)
randomnode(net,s)
randomnode_f(net)
randomnode_f(net,s)
```

*net* からランダムなノードの ID を返します。

第二引数 *s* が指定されていない場合、ノードはネットワーク内のすべてのノードから均等に選ばれます。 *s* が整数の場合、ノードは状態 *s* のノードから均等に選ばれます。 *s* が整数の配列またはタプルの場合、ノードはリストされた状態のノードから均等に選ばれます。

この関数は、*s* が整数または省略された場合、定数時間で実行されます。 *s* が配列またはタプルの場合、最悪のパフォーマンスはノード状態の数にのみ依存します。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

この関数の安全なバージョンは、空の集合からノードを選ぼうとしたときに、情報を含むエラーメッセージとともに ArgumentError をスローします。高速 (_f) バージョンでは、空の集合からノードを選ぼうとすると、ArgumentError がスローされますが、この場合のメッセージは「Range must be non-empty」のようになります。

また、[node](#Fastnet.node) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> makenodes!(net,100,1);

julia> makenodes!(net,100,2);

julia> nodestate(net,randomnode(net,1))
1
julia> nodestate(net,randomnode(net,2))
2
```
