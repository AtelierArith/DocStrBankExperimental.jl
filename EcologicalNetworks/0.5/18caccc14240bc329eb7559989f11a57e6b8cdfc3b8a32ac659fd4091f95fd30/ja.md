```
ρ(N::T; range=EcologicalNetworks.ρ_ska) where {T <: UnipartiteNetwork}
```

は、相互作用が正またはゼロである任意の一部ネットワークの隣接行列の固有値の実部の最大値の絶対値であるスペクトル半径を返します。スペクトル半径は行列の鏡像版で測定されるため、iからjへの相互作用はjからiへの相互作用も意味します。

スペクトル半径は、Staniczenko *et al.* (2013) によってネスト性の尺度として提案されています。Phillips (2011) は、システムが摂動を抑制または吸収する能力の尺度として使用しています。

#### 最大値

スペクトル半径はネットワークのサイズに敏感であり、ある程度はリンクの数にも敏感です。キーワード引数 `range` は、スペクトル半径の範囲版を返すため、最大値に対して相対的に表現されます。`range` 引数は *関数* を取り、2つの引数を必要とします：ネットワーク（単一部でなければなりません）とスペクトル半径の値です。

`EcologicalNetworks.jl` に付属するオプション（ここでLはリンクの数、Sはノードの数）は次の通りです：

1. `EcologicalNetworks.ρ_phillips`: (2L(S-1))/S の平方根で割ります。Phillips (2010) のように。
2. `EcologicalNetworks.ρ_ska`: Lの平方根で割ります。Staniczenko *et al.* (2013) のように - これは **デフォルト** であり、リンクの数の平方根の上限があります。
3. `EcologicalNetworks.ρ_raw`: 生の値を返します。

#### 参考文献

  * Phillips, J.D., 2011. The structure of ecological state transitions: Amplification, synchronization, and constraints in responses to environmental change. Ecological Complexity, 8, 336–346. https://doi.org/10.1016/j.ecocom.2011.07.004
  * Staniczenko, P.P.A., Kopp, J.C., Allesina, S., 2013. The ghost of nestedness in ecological networks. Nat Commun 4, 1391. https://doi.org/10.1038/ncomms2422
