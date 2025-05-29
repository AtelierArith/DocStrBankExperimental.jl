```
properties(chord::Array{<:Real,1}, tw_aero_d::Array{<:Real,1},
tw_prime_d::Array{<:Real,1}, le_loc::Real, xnode::Array{<:Real,1},
ynode::Array{<:Real,1}, e1::Array{<:Real,1}, e2::Array{<:Real,1},
g12::Array{<:Real,1}, anu12::Array{<:Real,1}, density::Array{<:Real,1},
xsec_nodeU::Array{<:Real,1}, n_laminaU::Array{Int64,1},
n_pliesU::Array{Int64,1}, t_lamU::Array{<:Real,1},
tht_lamU::Array{<:Real,1}, mat_lamU::Array{Int64,1},
xsec_nodeL::Array{<:Real,1}, n_laminaL::Array{Int64,1},
n_pliesL::Array{Int64,1}, t_lamL::Array{<:Real,1},
tht_lamL::Array{<:Real,1}, mat_lamL::Array{Int64,1},
loc_web::Array{<:Real,1}, n_laminaW::Array{Int64,1},
n_pliesW::Array{Int64,1}, t_lamW::Array{<:Real,1},
tht_lamW::Array{<:Real,1}, mat_lamW::Array{Int64,1})
```

複合材ブレードのスパン変動構造特性を計算します

# 入力

  * `chord::Real`: セクションの弦長 (m)
  * `tw_aero_d::Real`: セクションのねじれ角 (度)
  * `tw_prime_d::Real`: スパン位置に対するセクションのねじれ角の導関数 (度/m)
  * `le_loc::Real`: 参照軸に対する先端位置 (弦によって正規化)
  * `xnode::Array{<:Real,1}`: 先端から始まり上面を通り、再び下面を回るx翼型座標
  * `ynode::Array{<:Real,1}`: 先端から始まり上面を通り、再び下面を回るy翼型座標
  * `e1::Array{<:Real,1}`: E1
  * `e2::Array{<:Real,1}`: E2
  * `g12::Array{<:Real,1}`: G12
  * `anu12::Array{<:Real,1}`: Nu12
  * `density::Array{<:Real,1}`: 密度
  * `xsec_nodeU::Array{<:Real,1}`: 上面のセクタ境界の正規化された弦位置
  * `n_laminaU::Array{Int64,1}`: 上面の各セクタのラミナ数
  * `n_pliesU::Array{Int64,1}`: 上面のプライ数
  * `t_lamU::Array{<:Real,1}`: 上面のラミナのプライ厚さ (m)
  * `tht_lamU::Array{<:Real,1}`: 上面のラミナの方向 (度)
  * `mat_lamU::Array{Int64,1}`: 上面のラミナの材料ID
  * `xsec_nodeL::Array{<:Real,1}`: 下面のセクタ境界の正規化された弦位置
  * `n_laminaL::Array{Int64,1}`: 下面の各セクタのラミナ数
  * `n_pliesL::Array{Int64,1}`: 下面のプライ数
  * `t_lamL::Array{<:Real,1}`: 下面のラミナのプライ厚さ (m)
  * `tht_lamL::Array{<:Real,1}`: 下面のラミナの方向 (度)
  * `mat_lamL::Array{Int64,1}`: 下面のラミナの材料ID
  * `loc_web::Array{<:Real,1}`: ウェブのセクタ境界の正規化された弦位置
  * `n_laminaW::Array{Int64,1}`: ウェブの各セクタのラミナ数
  * `n_pliesW::Array{Int64,1}`: ウェブのプライ数
  * `t_lamW::Array{<:Real,1}`: ウェブのラミナのプライ厚さ (m)
  * `tht_lamW::Array{<:Real,1}`: ウェブのラミナの方向 (度)
  * `mat_lamW::Array{Int64,1}`: ウェブのラミナの材料ID

# 出力:

  * `eifbar`: ei_flap, YE軸に関するセクションのフラップ曲げ剛性 (Nm2)
  * `eilbar`: ei_lag, XE軸に関するセクションのラグ（エッジ方向）曲げ剛性 (Nm2)
  * `gjbar`: gj, セクションのねじり剛性 (Nm2)
  * `eabar`: ea, セクションの軸方向剛性 (N)
  * `eiflbar`: s_fl, XE-YEフレームに関する結合フラップ-ラグ剛性 (Nm2)
  * `sfbar`: s_af, XE-YEフレームに関する結合軸方向-フラップ剛性 (Nm)
  * `slbar`: s_al, XE-YEフレームに関する結合軸方向-ラグ剛性 (Nm.)
  * `sftbar`: s_ft, XE-YEフレームに関する結合フラップ-ねじり剛性 (Nm2)
  * `sltbar`: s_lt, XE-YEフレームに関する結合ラグ-ねじり剛性 (Nm2)
  * `satbar`: s_at, 結合軸方向-ねじり剛性 (Nm)
  * `z_sc`: x_sc, XR-YR軸に関するせん断中心オフセットのX座標 (m)
  * `y_sc`: y_sc, XR-YR参照フレームに対するセクションせん断中心の弦方向オフセット (m)
  * `ztc_ref`: x_tc, XR-YR軸に関するテンション中心オフセットのX座標 (m)
  * `ytc_ref`: y_tc, XR-YR軸に関するセクションテンション中心の弦方向オフセット (m)
  * `mass`: mass, 単位長さあたりのセクション質量 (Kg/m)
  * `iflap_eta`: flap_iner, 単位長さあたりのYG軸に関するセクションフラップ慣性 (Kg-m)
  * `ilag_zeta`: lag_iner, 単位長さあたりのXG軸に関するセクションラグ慣性 (Kg-m)
  * `tw_iner_d`: tw*iner*d, ブレード参照平面に対するセクション主慣性軸の方向, θ (度)
  * `zcm_ref`: x_cm, XR-YR軸に関する質量中心オフセットのX座標 (m)
  * `ycm_ref`: y_cm, XR-YR軸に関するセクション質量中心の弦方向オフセット (m)
  * `n_af_nodes`: 翼型ノードの数
  * `n_materials`: 材料の数
  * `n_sctU`: 上面のセクタ数
  * `n_sctL`: 下面のセクタ数
  * `nwebin`: ウェブの数
  * `n_laminaTotalU`: 上面のラミナの総数
  * `n_laminaTotalL`: 下面のラミナの総数
  * `n_laminaTotalW`: ウェブのラミナの総数
