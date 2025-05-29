```julia
ptn_2d(     Pat::Union{Pattern,Vector{<:Pattern}};     ind::Union{Int,Vector{Int}} = 1,     dims::Union{Int,Vector{Int}} = 1,     type::String = "normal",     xlabel::String = "",     ylabel::String = "",     xrange::Vector{<:Real} = [0, 0],     yrange::Vector{<:Real} = [0, 0],     trange::Vector{<:Real} = [0, 0],     rrange::Vector{<:Real} = [0, 0],     width::Real = 0,     height::Real  = 0,     mode::Union{String,Vector{String}} = "lines",     color::Union{String,Vector{String}} = "",     name::Union{String,Vector{String}}  = "", )

2D放射パターンをプロットします。キーワード`ind`と`dim`を設定することで実現します。例えば、`dim=1`を設定すると`U[:, ind]`のスライスを取得し、`dim=2`を設定すると`U[ind, :]`のスライスを取得します。また、2つ以上のパターンを比較するためにも使用できます（例として`ex_basics.jl`と`ex_horn.jl`を参照）。2つ以上のパターンカットを比較する際には、これらのキーワードをベクトルとして設定することで、異なる`ind`、`dims`、`mode`、`color`、`name`を指定できます（設定しない場合はデフォルト値が使用されます）。

#### 引数

  * `Pat`: `Pattern`または`Pattern`のベクトル
  * `ind`: パターンをスライスするためのインデックス（デフォルト: `1`）
  * `dims`: パターンをスライスする次元、`1`または`2`（デフォルト: `1`）
  * `type`: プロットタイプ、`"normal"`または`"polar"`（デフォルト: `"normal"`）
  * `xlabel`: x軸のラベル（デフォルト: `""`）
  * `ylabel`: y軸のラベル（デフォルト: `""`）
  * `xrange`: x軸の範囲（デフォルト: `[0, 0]`）
  * `yrange`: y軸の範囲（デフォルト: `[0, 0]`）
  * `trange`: 角度軸の範囲（デフォルト: `[0, 0]`）
  * `rrange`: 半径軸の範囲（デフォルト: `[0, 0]`）
  * `width`: プロットの幅（デフォルト: `0`）
  * `height`: プロットの高さ（デフォルト: `0`）
  * `mode`: プロットモード（デフォルト: `"lines"`)
  * `color`: プロット線の色（デフォルト: `""`）
  * `name`: プロット線の名前（デフォルト: `""`）
```
