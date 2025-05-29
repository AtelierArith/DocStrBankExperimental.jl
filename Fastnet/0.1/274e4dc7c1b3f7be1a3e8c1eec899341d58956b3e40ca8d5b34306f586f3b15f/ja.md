```
countnodes(net)
countnodes(net,s)
countnodes_f(net)
countnodes_f(net,s)
```

状態 *s* のノードをカウントします。状態が提供されていない場合は、ネットワーク全体のノードをカウントします。

状態 *s* の代わりに、状態の配列またはタプルを渡すこともできます。この場合、リストされたすべての状態のノードの合計数が返されます。

この関数のすべてのバージョンは定数時間で実行されます。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

パフォーマンスが重要な場合は、この関数を使用してください。nodecounts よりもこちらの方が良いです。

また、[nodecounts](#Fastnet.nodecounts) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> for i=1:20
         makenode!(net,1)
         end

julia> for i=1:10
         makenode!(net,2)
         end

julia> countnodes(net)
30

julia> countnodes(net,1)
20

julia> countnodes(net,(1,2))
30
```
