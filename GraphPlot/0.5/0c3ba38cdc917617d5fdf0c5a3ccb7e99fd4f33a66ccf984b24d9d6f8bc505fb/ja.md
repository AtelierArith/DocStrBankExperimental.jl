与えられたグラフと2つのXおよびY座標のベクトルに基づいて、グラフレイアウトのComposeツリーを返します。

**引数**

`G` 描画するグラフ

`layout` オプション。レイアウトアルゴリズム。現在、[`random_layout`, `circular_layout`, `spring_layout`, `shell_layout`, `stressmajorize_layout`, `spectral_layout`]のいずれかです。デフォルト: `spring_layout`

`locs_x, locs_y` ノードの位置。任意の単位を使用できますが、いずれにせよ正規化されて中央に配置されます。

`NODESIZE` オプション。ノードの最大サイズ。デフォルト: `3.0/sqrt(N)`

`nodesize` オプション。ノードの相対サイズ、ベクトルで指定できます。デフォルト: `1.0`

`nodelabel` オプション。頂点のラベル、ベクトルまたは何も指定しないことができます。デフォルト: `nothing`

`nodelabelc` オプション。ノードラベルの色、ベクトルで指定できます。デフォルト: `colorant"black"`

`nodelabeldist` オプション。ノードの中心からノードラベルまでの距離。デフォルト: `0.0`

`nodelabelangleoffset` オプション。ノードラベルの角度オフセット。デフォルト: `π/4.0`

`NODELABELSIZE` オプション。頂点ラベルの最大フォントサイズ。デフォルト: `4.0`

`nodelabelsize` オプション。頂点ラベルの相対フォントサイズ、ベクトルで指定できます。デフォルト: `1.0`

`nodefillc` オプション。ノードを塗りつぶす色、ベクトルで指定できます。デフォルト: `colorant"turquoise"`

`nodestrokec` オプション。ノードのストロークの色、ベクトルで指定できます。デフォルト: `nothing`

`nodestrokelw` オプション。ノードのストロークの線幅、ベクトルで指定できます。デフォルト: `0.0`

`edgelabel` オプション。エッジのラベル、ベクトルまたは何も指定しないことができます。デフォルト: `[]`

`edgelabelc` オプション。エッジラベルの色、ベクトルで指定できます。デフォルト: `colorant"black"`

`edgelabeldistx, edgelabeldisty` オプション。エッジの中心からエッジラベルまでの距離。デフォルト: `0.0`

`EDGELABELSIZE` オプション。エッジラベルの最大フォントサイズ。デフォルト: `4.0`

`edgelabelsize` オプション。エッジラベルの相対フォントサイズ、ベクトルで指定できます。デフォルト: `1.0`

`EDGELINEWIDTH` オプション。エッジの最大線幅。デフォルト: `0.25/sqrt(N)`

`edgelinewidth` オプション。エッジの相対線幅、ベクトルで指定できます。デフォルト: `1.0`

`edgestrokec` オプション。エッジのストロークの色、ベクトルで指定できます。デフォルト: `colorant"lightgray"`

`arrowlengthfrac` オプション。矢印に使用する線の長さの割合。無向グラフの場合は0に等しい。デフォルト: 有向グラフの場合は`0.1`

`arrowangleoffset` オプション。矢印の角度幅（ラジアン）。デフォルト: `π/9 (20度)`
