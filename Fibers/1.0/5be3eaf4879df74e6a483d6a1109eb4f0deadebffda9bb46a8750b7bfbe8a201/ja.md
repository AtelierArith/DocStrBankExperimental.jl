```
StreamWork{T}
```

ストリームライントラクトグラフィのための事前割り当てされたワークスペース

  * `T::DataType`      : データ型 (デフォルト: `Float32`)
  * `len_min::Int`     : 最小ストリームライン長 (デフォルト: 3)
  * `len_max::Int`     : 最大ストリームライン長 (デフォルト: max(nx,ny,nz))
  * `cosang_thresh::T` : 最大曲がり角のコサイン (デフォルト: cosd(45))
  * `step_size::T`     : ステップ長、ボクセル単位 (デフォルト: .5 ボクセル)
  * `smooth_coeff::T`  : ベクトルスムージング係数、[0-1]の範囲 (デフォルト: .2)
  * `micro_search_cosang::T`         : 探索角のコサイン (デフォルト: cosd(10))
  * `micro_search_dist::Vector{Int}` : 探索距離、ボクセル単位 (デフォルト: 15)
  * `strdims::Vector{Int}`  : 2D LCMの平面内寸法 [2]
  * `dxyz::Matrix{Int}`     : LCMにおけるボクセルジャンプの座標増分 [3 4]
  * `edgetype::Matrix{Int}` : i番目のLCM要素によって接続されたボクセルエッジ [2 10]
  * `mask::BitArray{3}`            : 脳マスク (ボクセル単位) [nx ny nz]
  * `ovecs::Array{T, 5}`           : 向きベクトル [3 nvec nx ny nz]
  * `lcms::Array{T, 4}`            : LCM要素 [nmat nx ny nz]
  * `sublist::Vector{Vector{T}}`   : サブボクセルサンプリングオフセット [nsub][3]
  * `pos_now::Vector{Vector{T}}`   : 現在の (x, y, z) 位置 [ncore][3]
  * `vec_now::Vector{Vector{T}}`   : 現在の向きベクトル [ncore][3]
  * `pos_next::Vector{Vector{T}}`  : 次の (x, y, z) 位置 [ncore][3]
  * `vec_next::Vector{Vector{T}}`  : 次の向きベクトル [ncore][3]
  * `ivec_next::Vector{Int}`       : 次の向きベクトルのインデックス [ncore]
  * `cosang::Vector{Vector{T}}`    : ベクトル間の角度のコサイン [ncore][nvec]
  * `cosangabs::Vector{Vector{T}}` : 上記の絶対値 [ncore][nvec]
  * `dvox::Vector{Vector{Int}}`    : ボクセル位置の変化 [ncore][3]
  * `lcm::Vector{Vector{T}}`       : 単一ボクセルでのLCMベクトル [ncore][10]
  * `isdiff::Vector{Bool}`         : メソッドの違いの指標 [ncore]
  * `str::Vector{Vector{Matrix{T}}}`     : ストリームライン [ncore][nstr][3 npts]
  * `flag::Vector{Vector{Vector{Bool}}}` : ストリームラインのフラグ [ncore][nstr][npts]
