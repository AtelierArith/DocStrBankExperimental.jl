引数:

  * `x::AbstractVector{<:Real}`: 主衛星（観測衛星）の慣性状態（位置と速度）
  * `xrtn::SVector{6,<:Real}`: 対象衛星の慣性状態（位置と速度）

返り値:

  * `xt::SVector{6,<:Real}`: RTNにおける観測衛星に対する対象の位置と速度。
