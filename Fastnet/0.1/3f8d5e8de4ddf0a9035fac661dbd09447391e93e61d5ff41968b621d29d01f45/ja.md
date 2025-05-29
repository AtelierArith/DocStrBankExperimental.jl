```
randomlink(net)
randomlink(net,s)
randomlink_f(net)
randomlink_f(net,s)
```

*net* からランダムにリンクの ID を返します。

第二引数 *s* が指定されていない場合、リンクはネットワーク内のすべてのリンクから均等に選ばれます。 *s* が整数の場合、リンクは状態 *s* のリンクから均等に選ばれます。 *s* が整数の配列またはタプルの場合、リンクはリストされた状態のリンクから均等に選ばれます。

この関数は、*s* が整数または省略された場合、定数時間で実行されます。 *s* が配列またはタプルの場合、最悪のパフォーマンスは追跡されたリンク状態の数にのみ依存します。 高速 (_f) バージョンは、パフォーマンス向上のためにいくつかの安全チェックを犠牲にしています。 詳細については [basic concepts](concepts.md) を参照してください。

この関数の安全なバージョンは、空の集合からリンクを選ぼうとしたときに、情報を含むエラーメッセージとともに ArgumentError をスローします。 高速 (_f) バージョンでは、空の集合からリンクを選ぼうとすると、ArgumentError がスローされますが、この場合のメッセージは「Range must be non-empty」のようになります。

また、[link](#Fastnet.link) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(2,2,2)])
ノード数 0、リンク数 0 のネットワーク

julia> randomgraph!(net);

julia> for i=1:500
         nd=randomnode(net,1)
         nodestate!(net,nd,2)
       end

julia> lnk=randomlink(net,1);

julia> linkstate(net,lnk)
1
```
