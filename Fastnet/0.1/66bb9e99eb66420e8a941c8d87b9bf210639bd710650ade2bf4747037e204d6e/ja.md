link(net,rp) link(net,s,rp) link*f(net,rp) link*f(net,s,rp)

相対位置 *rp* とノード状態 *s* からリンクIDを決定します。

リンク関数は、特定のリンク状態にあるノードのセットからリンクにアクセスする方法、またはすべてのリンクのセットからリンクにアクセスする方法を提供します。2引数バージョンは、ネットワーク *net* の位置 *rp* にあるリンクのIDを返します。3引数バージョンは、状態 *s* にあるリンクのセット内の位置 *rp* にあるリンクのIDを返します。

この関数のすべてのバージョンは定数時間で実行されますが、高速 (_f) バージョンはパフォーマンス向上のためにいくつかの安全チェックを犠牲にします。詳細については [基本概念](concepts.md) を参照してください。

また、[adjacent](#Fastnet.adjacent) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(1000,2000,2,[LinkType(1,2),LinkType(1,1),LinkType(2,2)])
Network of 0 nodes and 0 links

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,1);

julia> n3=makenode!(net,2);

julia> makelink!(net,n1,n2);

julia> makelink!(net,n2,n3);

julia> makelink!(net,n3,n1);

julia> lid=link(net,2,1);

julia> linkdst(net,lid)==n2
true

julia> linksrc(net,lid)==n1
true
```
