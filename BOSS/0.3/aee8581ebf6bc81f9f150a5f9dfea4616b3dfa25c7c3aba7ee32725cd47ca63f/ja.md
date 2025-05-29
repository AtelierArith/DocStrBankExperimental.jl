ライブラリ/アルゴリズムを指定して、獲得関数の最適化に使用します。このタイプを継承してカスタム獲得最大化器を定義します。

例: `struct CustomAlg <: AcquisitionMaximizer ... end`

すべての獲得最大化器は次のことを実装する必要があります: `maximize_acquisition(acq_maximizer::CustomAlg, acq::AcquisitionFunction, problem::BossProblem, options::BossOptions)`。

このメソッドはタプル `(x, val)` を返します。返される `x` は、与えられた獲得関数 `acq` を最大化する入力ドメインの点（ベクトルとして）または点のバッチ（列ごとの行列として）です。返される `val` は獲得値 `acq(x)`、またはバッチの各点に対する値 `acq.(eachcol(x))`、または `nothing`（獲得最大化器の実装に依存）です。

参照: [`OptimizationAM`](@ref)
