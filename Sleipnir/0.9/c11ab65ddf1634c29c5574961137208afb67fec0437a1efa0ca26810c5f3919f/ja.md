```
mutable struct Results{F <: AbstractFloat, I <: Int}
```

シミュレーションの結果を格納するための可変構造体です。

# フィールド

  * `rgi_id::String`: RGI（ランドルフ氷河在庫）の識別子。
  * `H::Vector{Matrix{F}}`: 時間にわたる氷河の氷厚 `H` を表す行列のベクトル。
  * `H_glathida::Matrix{F}`: グラシダ氷厚のためのオプションの行列。
  * `H_ref::Union{Nothing, Vector{Matrix{F}}}`: 氷厚の参照データ。
  * `S::Matrix{F}`: 氷河の表面高度計測。
  * `B::Matrix{F}`: 氷河の基盤岩。
  * `V::Matrix{F}`: 氷河の氷表面速度。
  * `Vx::Matrix{F}`: 氷河の氷表面速度 `V` の x成分。
  * `Vy::Matrix{F}`: 氷河の氷表面速度 `V` の y成分。
  * `V_ref::Union{Nothing, Matrix{F}}`: 氷河の氷表面速度 `V` の参照データ。
  * `Vx_ref::Union{Nothing, Matrix{F}}`: 氷河の氷表面速度 `Vx` の x成分の参照データ。
  * `Vy_ref::Union{Nothing, Matrix{F}}`: 氷河の氷表面速度 `Vy` の y成分の参照データ。
  * `Δx::F`: x方向のグリッド間隔。
  * `Δy::F`: y方向のグリッド間隔。
  * `lon::Union{Nothing, F}`: オプションの経度値。
  * `lat::Union{Nothing, F}`: オプションの緯度値。
  * `nx::I`: x方向のグリッドポイントの数。
  * `ny::I`: y方向のグリッドポイントの数。
  * `tspan::Vector{F}`: シミュレーションの時間範囲。
  * `θ::Union{Nothing, ComponentArray{F}}`: 機械学習モデルのパラメータ。
  * `loss::Union{Nothing, Vector{F}}` 損失関数の進化を示すベクトル。
