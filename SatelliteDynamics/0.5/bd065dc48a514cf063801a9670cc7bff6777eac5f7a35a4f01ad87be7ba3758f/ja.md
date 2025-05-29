RK4は、関数のシグネチャf(epc, x,...; kwargs...)を格納し、その関連設定パラメータを持つ数値積分オブジェクトです。

引数:

  * `f::Function` 積分のための関数。
  * `auxParams::Dict`
