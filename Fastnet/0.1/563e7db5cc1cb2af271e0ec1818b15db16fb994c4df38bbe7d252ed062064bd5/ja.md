```
regulargraph!(net::FastNet,deg;<keyword arguments>)
```

ノードの次数 *deg* を持つ正則グラフを作成します。

*net* のネットワークは、すべてのノードが次数 *deg* を持ち、ランダムに接続された新しいトポロジーに置き換えられます。ノードの数が指定されていない場合、関数は net によって許可されるすべてのノードを使用しようとします。

ネットワーク生成は高速で偏りがありませんが、単純なグラフになることは保証されていません。

奇数のノード次数と奇数のノード数を持つ有限正則グラフは存在しないことに注意してください。したがって、*deg* またはノードの数のいずれかは偶数でなければなりません。

FastNet が希望するリンクまたはノードの数を収容するのに十分大きくない場合、引数エラーが発生します。

キーワード引数は次のとおりです。

  * N : ネットワークの作成に使用されるノードの数
  * S : ノードの状態。すべてのノードはこの状態に設定されます。

# 例

```jldoctest
julia> using Fastnet

julia>  net=FastNet(1000,2000,2,[])
Network of 0 nodes and 0 links

julia> regulargraph!(net,4)
Network of 1000 nodes and 2000 links

julia> degreedist(net)
4-element Vector{Float64}:
 0.0
 0.0
 0.0
 1.0
```
