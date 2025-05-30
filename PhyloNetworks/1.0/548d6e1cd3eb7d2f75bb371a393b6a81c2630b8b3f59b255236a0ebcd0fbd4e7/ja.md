```
getnodeheights_majortree(net, checkpreorder::Bool=true; warn=true)
```

メジャーツリーからのノードの高さのベクトル、すなわち、ノードの高さを考慮したときのルートから各ノードまでの距離。

欠損エッジの長さ:

  * ツリーエッジに欠損エッジの長さがある場合、エラーが発生します。
  * 特定のハイブリッドノードにおいてすべての親ハイブリッドエッジに欠損長さがある場合、そのハイブリッドノードはルートにできるだけ近いと見なされ、すなわち、リティキュレーションは長さ0のハイブリッドエッジの1つで「ジップアップ」されていると見なされます。
  * メジャーハイブリッドエッジに欠損長さがある場合、ハイブリッドノードの高さは、最大の継承γを持つマイナー親のノードの高さとエッジの長さを使用して計算されます（警告付き）。メジャーハイブリッドエッジに長さが欠けていて、すべての欠損していないマイナーエッジが継承γを欠いているか、同じ値を持っている場合、エラーが発生します。

ネットワークが時間的一貫性を持たない場合、`warn=false`でない限り、警告が発行されます。

参照: [`istimeconsistent`](@ref)、[`getnodeheights`](@ref) および [`getnodeheights_average`](@ref)。

```jldoctest
#時間的一貫性のあるネットワークのノードの高さは同じ
julia> consistent_net = readnewick("((A:2.5,#H1:1.5::0.4):0.25,(C:1.5,(B:1)#H1:0.5::0.6):1.25);");

julia> heights = getnodeheights(consistent_net)
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 1.75
 2.75
 2.75

julia> heights_average = getnodeheights_average(consistent_net);

julia> heights_major = getnodeheights_majortree(consistent_net);

julia> heights == heights_average == heights_major  
true
```

```jldoctest
#不一致なネットワークは異なる結果を与える
julia> inconsistent_net = readnewick("((A:2.5,#H1:1.5::0.4):0.25,(C:1.5,(B:1)#H1:2.5::0.6):1.25);");

julia> getnodeheights_average(inconsistent_net;warn=false)
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 2.95
 3.95
 2.75

julia> getnodeheights_majortree(inconsistent_net;warn=false) 
7-element Vector{Float64}:
 0.0
 1.25
 2.75
 0.25
 3.75
 4.75
 2.75

```
