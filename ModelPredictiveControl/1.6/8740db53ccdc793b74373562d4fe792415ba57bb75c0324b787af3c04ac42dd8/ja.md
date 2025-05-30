```
setmodel!(estim::StateEstimator, model=estim.model; <keyword arguments>) -> estim
```

`estim` [`StateEstimator`](@ref) の `model` と共分散行列を設定します。

ランタイムでの [`LinModel`](@ref) に基づく推定器のモデル適応を可能にします。 [`NonLinModel`](@ref) の状態空間関数の変更はサポートされていません。新しい共分散行列はキーワード引数で指定できます（命名法については [`SteadyKalmanFilter`](@ref) のドキュメントを参照してください）。 [`Luenberger`](@ref) および [`SteadyKalmanFilter`](@ref) ではサポートされていないため、時間変化する [`KalmanFilter`](@ref) を代わりに使用してください。 [`MovingHorizonEstimator`](@ref) モデルは推定ホライズン $H_e$ の間一定に保たれます。行列の次元とサンプル時間は同じでなければなりません。新しい拡張モデルの可観測性と制御可能性は検証されないことに注意してください（詳細については拡張ヘルプを参照してください）。

# 引数

!!! info
    *`強調`* されたキーワード引数は非Unicodeの代替です。


  * `estim::StateEstimator` : モデルと共分散を設定する推定器。
  * `model=estim.model` : 新しいプラントモデル（[`NonLinModel`](@ref) ではサポートされていません）。
  * `Q̂=nothing` または *`Qhat`* : 新しい拡張モデル $\mathbf{Q̂}$ の共分散行列。
  * `R̂=nothing` または *`Rhat`* : 新しい拡張モデル $\mathbf{R̂}$ の共分散行列。

# 例

```jldoctest
julia> kf = KalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0)), σQ=[√4.0], σQint_ym=[√0.25]);

julia> kf.model.A[], kf.Q̂[1, 1], kf.Q̂[2, 2] 
(0.1, 4.0, 0.25)

julia> setmodel!(kf, LinModel(ss(0.42, 0.5, 1, 0, 4.0)), Q̂=[1 0;0 0.5]);

julia> kf.model.A[], kf.Q̂[1, 1], kf.Q̂[2, 2] 
(0.42, 1.0, 0.5)
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    [`default_nint`](@ref) メソッドによって計算されたデフォルトのモデル拡張を使用すると、非積分プラントモデルから積分モデルに切り替えると、可観測でない拡張モデルが生成されます。モデル入力で未測定の外乱を移動させる（`nint_u` パラメータ）ことで、この問題を解決できます。

