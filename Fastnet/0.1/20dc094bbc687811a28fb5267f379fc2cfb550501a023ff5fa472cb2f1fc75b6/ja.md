```
simstep!(sim)
```

*sim* の次のイベントをシミュレートします。

この関数は常にシミュレーションを正確に1つのイベントだけ進めます。イベントが発生しない場合は、時間を1タイムユニット進めます。出力は開始時刻とイベントが発生した直後に生成されます。

[FastSim](#Fastnet.FastSim)や[simstep](#Fastnet.simstep)も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(2,1,2,[])
ノード数0、リンク数0のネットワーク

julia> n1=makenode!(net,1);

julia> n2=makenode!(net,2);

julia> function rates!(r,t)
         r[1]=countnodes(net,2)
         end
rates! (generic function with 1 method)

julia> function simpleproc!()
         node=randomnode(net,2)
         nodestate!(net,node,1)
         end
simpleproc! (generic function with 1 method)

julia> sim=FastSim(net,rates!,[simpleproc!]; output=false)
シミュレーションが実行中、現在の時間は0.0です

julia> simstep!(sim)

julia> nodecounts(net)
2-element Vector{Int64}:
 2
 0
```
