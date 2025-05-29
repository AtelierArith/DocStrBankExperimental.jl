引数:

  * `x::AbstractVector{<:Real}`: 主衛星（観測衛星）の慣性状態（位置と速度）
  * `xt::SVector{3,<:Real}`: 対象衛星の慣性状態（位置）

戻り値:

  * `xrtn::SVector{3,<:Real}`: RTNにおける観測衛星に対する対象衛星の相対位置。
