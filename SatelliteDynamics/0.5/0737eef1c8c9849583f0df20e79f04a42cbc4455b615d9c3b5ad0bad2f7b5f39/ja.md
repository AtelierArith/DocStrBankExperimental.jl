オイラー角をベクトルとして返します。

`EulerAngle` `e` に対して、次のように等価です: `[e.phi, e.theta, e.psi]`

引数:

  * `e::EulerAngle` オイラー角

返すもの:

  * `evec::AbstractArray{Float64, 1}` ベクトル形式のオイラー角の成分。
