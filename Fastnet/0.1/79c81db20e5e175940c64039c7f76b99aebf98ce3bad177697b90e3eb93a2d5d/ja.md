```
countlinks(net)
countlinks(net,s)
countlinks_f(net)
countlinks_f(net,s)
```

状態 *s* のリンクをカウントします。状態が提供されていない場合は、ネットワーク全体のリンクをカウントします。

状態 *s* の代わりに、状態の配列またはタプルを渡すこともできます。この場合、リストされたすべての状態のノードの合計数が返されます。

単一のクラスまたはネットワーク全体のリンクは、定数時間でカウントされます。タプルまたは配列の引数の場合、パフォーマンスはタプル/配列の要素数に比例してスケールします。高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。詳細については [basic concepts](concepts.md) を参照してください。

パフォーマンスが重要な場合は、この関数を使用してください。linkcounts よりもこちらの方が良いです。

また、[linkcounts](#Fastnet.linkcounts) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2,1),LinkType(2,2,2)])
Network of 0 nodes and 0 links

julia> makenodes!(net,20,1)

julia> makenodes!(net,20,2)

julia> for i=1:20
         from=node(net,1,i)
         to=node(net,2,i)
         makelink!(net,from,to)
       end

julia> makelink!(net,node(net,2,1),node(net,2,2));

julia> countlinks(net)
21

julia> countlinks(net,1)
20

julia> countlinks(net,2)
1

julia> countlinks(net,[1,2])
21
```
