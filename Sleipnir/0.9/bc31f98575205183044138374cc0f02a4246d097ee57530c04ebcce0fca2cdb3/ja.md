```
氷河シミュレーションのための `Results` オブジェクトを構築します。

# 引数

  * `glacier::G`: 氷河オブジェクト、`AbstractGlacier` のサブタイプ。
  * `ifm::IF`: モデルオブジェクト、`AbstractModel` のサブタイプ。
  * `rgi_id::String`: 氷河の RGI 識別子。デフォルトは `glacier.rgi_id`。
  * `H::Union{Nothing, Vector{Matrix{F}}}`: 氷の厚さ行列。デフォルトは何も設定されていません。
  * `H_glathida::Matrix{F}`: GlaThiDa からの氷の厚さ。デフォルトは `glacier.H_glathida`。
  * `H_ref::Union{Nothing, Vector{Matrix{F}}}`: 参照氷の厚さ。デフォルトは何も設定されていません。
  * `S::Union{Nothing, Matrix{F}}`: 表面標高行列。デフォルトは `ifm.S` と同じサイズのゼロ行列。
  * `B::Union{Nothing, Matrix{F}}`: 床標高行列。デフォルトは `glacier.B` と同じサイズのゼロ行列。
  * `V::Union{Nothing, Vector{Matrix{F}}}`: 速度の大きさ行列。デフォルトは何も設定されていません。
  * `Vx::Union{Nothing, Vector{Matrix{F}}}`: x方向の速度行列。デフォルトは何も設定されていません。
  * `Vy::Union{Nothing, Vector{Matrix{F}}}`: y方向の速度行列。デフォルトは何も設定されていません。
  * `V_ref::Union{Nothing, Vector{Matrix{F}}}`: 参照速度の大きさ行列。デフォルトは何も設定されていません。
  * `Vx_ref::Union{Nothing, Vector{Matrix{F}}}`: 参照x方向の速度行列。デフォルトは何も設定されていません。
  * `Vy_ref::Union{Nothing, Vector{Matrix{F}}}`: 参照y方向の速度行列。デフォルトは何も設定されていません。
  * `Δx::F`: x方向のグリッド間隔。デフォルトは `glacier.Δx`。
  * `Δy::F`: y方向のグリッド間隔。デフォルトは `glacier.Δy`。
  * `lon::Union{Nothing, F}`: 氷河中心の経度。デフォルトは `glacier.cenlon`。
  * `lat::Union{Nothing, F}`: 氷河中心の緯度。デフォルトは `glacier.cenlat`。
  * `nx::I`: x方向のグリッドポイント数。デフォルトは `glacier.nx`。
  * `ny::I`: y方向のグリッドポイント数。デフォルトは `glacier.ny`。
  * `tspan::Tuple(F, F)`: シミュレーションの時間範囲。
  * `θ::Union{Nothing, ComponentArray{F}}`: モデルパラメータ。デフォルトは `nothing`。
  * `loss::Union{Nothing, Vector{F}}`: 損失値。デフォルトは `nothing`。

# 戻り値

  * `results::Results`: シミュレーション結果を含む `Results` オブジェクト。
```
