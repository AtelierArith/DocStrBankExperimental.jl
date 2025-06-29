```
getnodeheights_average(net, checkpreorder::Bool=true; warn=true)
```

ノードの平均高さのベクトル、すなわち、根から各ノードまでの平均距離。平均は、ハイブリッドエッジの継承値 γ を重みとして使用した加重平均です（利用可能な場合）。一部の親が γ の継承値を欠いているハイブリッドノードでは、等しい重みが使用されます（警告付き）。

欠損エッジ長:

  * エッジ長が欠損しているツリーエッジがある場合、エラーが発生します。
  * 特定のハイブリッドノードで全ての親ハイブリッドエッジが欠損している場合、そのハイブリッドノードは根にできるだけ近いと見なされ、すなわち、リティキュレーションは長さ0のハイブリッドエッジの1つで「ジップアップ」されていると見なされます。
  * 一部の親ハイブリッドエッジに欠損長があるが、全てではない場合、平均ノード高さは欠損のない親のみを基に計算されます。ハイブリッドノードの高さが親の高さのいずれかよりも低い場合（そのため、欠損長が負になる必要がある場合）、警告が発行されます。

ネットワークが時間的一貫性を持たない場合、`warn=false`でない限り警告が発行されます。

参照: [`istimeconsistent`](@ref)、[`getnodeheights`](@ref)、および `getnodeheights_majortree`](@ref)。
