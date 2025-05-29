地球中心を計算する

RTNフレームは、ローカル垂直・ローカル水平（LVLH）フレームとも一般的に呼ばれます。

引数:

  * `x::AbstractVector{<:Real}`: プライマリ（観測）衛星の慣性状態（位置と速度）
  * `xrtn::AbstractVector{<:Real}`: ターゲット衛星の慣性状態（位置と速度）

戻り値:

  * `xt::AbstractVector{<:Real}`: RTNにおける観測衛星に対するターゲットの位置と速度。
