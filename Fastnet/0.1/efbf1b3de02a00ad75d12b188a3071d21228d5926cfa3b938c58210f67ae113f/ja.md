```
runsim!(sim,dur,out=1.0)
```

シミュレーション *sim* を時間 *dur* の間実行し、間隔 *out* で出力を生成します。

シミュレーション中、FastSim とその関連する FastNet オブジェクトはネットワークの現在の状態を反映するように更新されます（ただし、シミュレーション時間に関する注意事項については、[こちら](#Fastnet.FastSim)を参照してください）。

この関数は、FastSim を **少なくとも** 特定の時間の間シミュレートします。シミュレーションの実行が終了する時点でまだイベントが発生している場合、シミュレーションは *dur* の後に発生する最初のイベントの直後に停止します。したがって、シミュレーション時間は常に *dur* より大きくなります。一般的に、差と実際のシミュレーション時間はわずかですが、イベントが非常にまれな場合、シミュレーションは *dur* を大幅に超えて実行されることがあります。この動作は、短い実行を繰り返し開始する際のウォッチドッグパラドックスのアーティファクトを回避するために必要です。

出力はシミュレーションの開始時に一度生成され、その後は *out* の倍数ごとに生成されます。たとえば、シミュレーション時間が実行開始時に *t=3.12* で、*dur=10* および *out=5* の場合、出力は 3.12、5、および 10 の時点で生成されます。その結果、ネットワークは最後の出力の統計とは異なる状態に残されます。

[FastSim](#Fastnet.FastSim) や [simstep!](#Fastnet.simstep!) も参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> net=FastNet(2,1,2,[])
ノード数 0、リンク数 0 のネットワーク

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
シミュレーション実行中、現在の時間は 0.0

julia> runsim!(sim,100)

julia> nodecounts(net)
2-element Vector{Int64}:
 2
 0
```
