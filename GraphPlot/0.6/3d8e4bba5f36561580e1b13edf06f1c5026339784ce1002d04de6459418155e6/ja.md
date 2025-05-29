与えられたグラフとXおよびY座標の2つのベクトルに基づいて、グラフレイアウトのComposeツリーを返します。

**引数**

`G` 描画するグラフ

`locs_x, locs_y` ノードの位置。任意の単位を使用できますが、いずれにせよ正規化されて中心に配置されます。提供されない場合は、`layout`キーワード引数から取得されます。

**キーワード引数**

`layout` レイアウトアルゴリズム。現在、[`random_layout`, `circular_layout`, `spring_layout`, `shell_layout`, `stressmajorize_layout`, `spectral_layout`]のいずれかです。デフォルト: `spring_layout`

`title` プロットタイトル。デフォルト: `""`

`title_color` プロットタイトルの色。デフォルト: `colorant"black"`

`title_size` プロットタイトルのサイズ。デフォルト: `4.0`

`font_family` すべてのテキストのフォントファミリー。デフォルト: `"Helvetica"`

`NODESIZE` ノードの最大サイズ。デフォルト: `3.0/sqrt(N)`

`nodesize` ノードの相対サイズ、ベクトルで指定できます。デフォルト: `1.0`

`nodelabel` 頂点のラベル、ベクトルまたは何も指定しない。デフォルト: `nothing`

`nodelabelc` ノードラベルの色、ベクトルで指定できます。デフォルト: `colorant"black"`

`nodelabeldist` ノードの中心からノードラベルまでの距離。デフォルト: `0.0`

`nodelabelangleoffset` ノードラベルの角度オフセット。デフォルト: `π/4.0`

`NODELABELSIZE` 頂点ラベルの最大フォントサイズ。デフォルト: `4.0`

`nodelabelsize` 頂点ラベルの相対フォントサイズ、ベクトルで指定できます。デフォルト: `1.0`

`nodefillc` ノードを塗りつぶす色、ベクトルで指定できます。デフォルト: `colorant"turquoise"`

`nodestrokec` ノードのストロークの色、ベクトルで指定できます。デフォルト: `nothing`

`nodestrokelw` ノードのストロークの線幅、ベクトルで指定できます。デフォルト: `0.0`

`edgelabel` エッジのラベル、ベクトルまたは何も指定しない。デフォルト: `[]`

`edgelabelc` エッジラベルの色、ベクトルで指定できます。デフォルト: `colorant"black"`

`edgelabeldistx, edgelabeldisty` エッジの中心からエッジラベルまでの距離。デフォルト: `0.0`

`EDGELABELSIZE` エッジラベルの最大フォントサイズ。デフォルト: `4.0`

`edgelabelsize` エッジラベルの相対フォントサイズ、ベクトルで指定できます。デフォルト: `1.0`

`EDGELINEWIDTH` エッジの最大線幅。デフォルト: `0.25/sqrt(N)`

`edgelinewidth` エッジの相対線幅、ベクトルで指定できます。デフォルト: `1.0`

`edgestrokec` エッジのストロークの色、ベクトルで指定できます。デフォルト: `colorant"lightgray"`

`arrowlengthfrac` 矢印に使用する線の長さの割合。無向グラフの場合は0に等しい。デフォルト: 有向グラフの場合は`0.1`

`arrowangleoffset` 矢印の角度幅（ラジアン）。デフォルト: `π/9 (20度)`

`linetype` エッジに使用される線のタイプ（"straight", "curve"）。デフォルト: "straight"

`outangle` エッジの角度幅（ラジアン）（`linetype = "curve"`の場合のみ使用）。デフォルト: `π/5 (36度)`

`background_color` プロット背景の色。デフォルト: `nothing`

`plot_size` プロットエリアの幅x高さのタプル。デフォルト: `(10cm, 10cm)`

`leftpad, rightpad, toppad, bottompad` プロットのマージンのパディング。デフォルト: `0mm`

`pad` プロットマージンのパディング（指定された場合は個別のパディングを上書きします）。デフォルト: `nothing`
