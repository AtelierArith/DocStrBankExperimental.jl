```
estimatemse(circ, pstr::PauliString, n_mcsamples::Integer, thetas=π; stateoverlapfunc=overlapwithzero, circuit_is_reversed=false, customtruncfunc=nothing)
```

モンテカルロサンプリングを使用して切り捨てられた回路シミュレーションの平均二乗誤差を推定する関数です。各`PauliRotation`の角度`theta`の`thetas`∈ [theta, theta]にわたって平均化された切り捨てられたパウリ伝播シミュレーションの平均二乗誤差を返します。現在、この関数は`PauliRotation`および`CliffordGate`ゲートを持つ回路のみをサポートしています。

`thetas`ベクトルの長さは、回路内のパラメータ化されたゲートの数と等しくする必要があります。あるいは、`thetas`はすべてのパラメータ化されたゲートに適用可能な単一の実数であることもできます。デフォルトの`thetas=π`または他の配列でない値は、回路が`PauliRotation` - `CliffordGate`のみで構成されていると仮定します。`PauliRotation`の場合、値はゼロ周りのパラメータの積分範囲である必要があります。

初期状態の重なりを計算するために、初期状態との逆伝播されたパウリ文字列の重なりを計算するための初期状態重なり関数`stateoverlapfunc`を提供できます。重要なことに、`kwargs`を使用してパウリ伝播の切り捨てパラメータを設定できます。現在サポートされているのは`max_weight`、`max_freq`、および`max_sins`です。ここでは`min_abs_coeff`はサポートされていないことに注意してください。角度にわたって統合された誤差を考慮するためです。`max_freq`は、平均して`thetas ∈ [-π, π]`の下で(1/2)^`max_freq`未満の小さな係数を効果的に切り捨てます。カスタム切り捨て関数は、シグネチャ`customtruncfunc(pstr::PauliStringType, coefficient)::Bool`を持つ`customtruncfunc`として渡すことができます。
