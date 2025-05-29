```
FastSim(net,rates!,processes;<keyword arguments>)
```

FastNetシミュレーションの実行を表すFastSim構造体を作成します。

最初の引数*net*は、シミュレーションで使用されるFastNet構造体です。

2番目の引数はシミュレーションの*rates!*関数です。rates関数は2つの引数を受け取る関数です。これらの引数の最初はMVector{Float64}です（詳細についてはStaticArrays Documentationを参照してください）。2番目の引数はシミュレーション内の現在の時間です。

*rates!*関数が呼び出されると、ネットワークの現在の状態に基づいて、システム内で異なるプロセスが発生する総レートを計算する必要があります。rates関数は、最初の引数として渡された配列を埋めることによってこれらの値を返します。rates!は戻り値を持たないべきです。

レートが時間依存である場合、rates!関数はシミュレーション構造から時間を取得するのではなく、渡された時間値を使用する必要があります。シミュレーションコードは、次のイベントまでレートが一定であると仮定しています。これはほとんどの場合無害ですが、レートが明示的に時間に依存している場合、レートが時間に非常に敏感であり、イベントが稀である場合には不正確さを引き起こす可能性があります。

3番目の引数は、プロセスを実装する関数のベクターです。プロセスは引数なしの関数であり、呼び出されるとそれぞれのプロセスが1回実行される効果を実装する必要があります。プロセス関数ベクターの要素は、*rates!*ベクターによって計算された対応するレートと同じ順序である必要があります。

FastSimは、いくつかのオプションのキーワード引数をサポートしています：

  * saveas : 結果を保存するパス名を指定する文字列。指定しない場合、結果は保存されませんが、*results*関数を使用して取得できます。
  * output : 結果をコンソールに印刷するかどうかを指定するブール変数。デフォルトではこれはtrueです。代わりに、結果を書き込むIOStreamを提供することもできます。
  * repfunc : この引数は、出力を生成し結果を保存するための代替関数を指定するために使用できます。詳細については[custimization](customization.md)を参照してください。

# 例

```jldoctest
julia> using Fastnet

julia> const Bored=1; const Excited=2;

julia> net=FastNet(1000,5000,2,[LinkType(Excited,Bored,1)]);

julia> randomgraph!(net);

julia> function rates!(rates,t)
         rates[1]=countlinks(net,1)*0.1
         rates[2]=countnodes(net,Excited)*0.2
         rates[3]=countnodes(net,Bored)*0.001
         end;

julia> function excitement_spreads()
         link=randomlink(net,1)
         nodestate!(net,linkdst(net,link),Excited)
         end;

julia> function get_bored()
         node=randomnode(net,Excited)
         nodestate!(net,node,Bored)
         end;

julia> function great_idea()
         node=randomnode(net,Bored)
         nodestate!(net,node,Excited)
         end;

julia> sim=FastSim(net,rates!,[excitement_spreads,get_bored,great_idea])
シミュレーション実行中、現在の時間は0.0です
```
