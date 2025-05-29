```
setmodel!(mpc::PredictiveController, model=mpc.estim.model; <keyword arguments>) -> mpc
```

`mpc` [`PredictiveController`](@ref) の `model` と目的関数の重みを設定します。

ランタイムでの [`LinModel`](@ref) に基づくコントローラのモデル適応を可能にします。 [`NonLinModel`](@ref) の状態空間関数の変更はサポートされていません。目的関数の新しい重み行列はキーワード引数で指定できます（命名法については [`LinMPC`](@ref) を参照）。もし `Cwt ≠ Inf` であれば、拡張移動抑制重みは $\mathbf{Ñ}_{H_c} = \mathrm{diag}(\mathbf{N}_{H_c}, C)$ となり、そうでなければ $\mathbf{Ñ}_{H_c} = \mathbf{N}_{H_c}$ となります。 [`StateEstimator`](@ref) `mpc.estim` は [`Luenberger`](@ref) オブザーバーまたは [`SteadyKalmanFilter`](@ref)（デフォルトの推定器）であってはなりません。代わりに時間変化する [`KalmanFilter`](@ref) で `mpc` オブジェクトを構築してください。モデルは予測ホライズン $H_p$ の間は一定であることに注意してください。

# 引数

!!! info
    *`強調`* されたキーワード引数は非Unicodeの代替です。


  * `mpc::PredictiveController` : モデルと重みを設定するコントローラ。
  * `model=mpc.estim.model` : 新しいプラントモデル（[`NonLinModel`](@ref) ではサポートされていません）。
  * `Mwt=nothing` : $\mathbf{M}$ 重み行列の新しい主対角成分（ベクトル）。
  * `Nwt=nothing` : $\mathbf{N}$ 重み行列の新しい主対角成分（ベクトル）。
  * `Lwt=nothing` : $\mathbf{L}$ 重み行列の新しい主対角成分（ベクトル）。
  * `M_Hp=nothing` : 新しい $\mathbf{M}_{H_p}$ 重み行列。
  * `Ñ_Hc=nothing` または *`Ntilde_Hc`* : 新しい $\mathbf{Ñ}_{H_c}$ 重み行列（上記の定義を参照）。
  * `L_Hp=nothing` : 新しい $\mathbf{L}_{H_p}$ 重み行列。
  * 追加のキーワード引数は `setmodel!(mpc.estim)` に渡されます。

# 例

```jldoctest
julia> mpc = LinMPC(KalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0)), σR=[√25]), Hp=1, Hc=1);

julia> mpc.estim.model.A[1], mpc.estim.R̂[1], mpc.weights.M_Hp[1], mpc.weights.Ñ_Hc[1]
(0.1, 25.0, 1.0, 0.1)

julia> setmodel!(mpc, LinModel(ss(0.42, 0.5, 1, 0, 4.0)); R̂=[9], M_Hp=[10], Nwt=[0.666]);

julia> mpc.estim.model.A[1], mpc.estim.R̂[1], mpc.weights.M_Hp[1], mpc.weights.Ñ_Hc[1]
(0.42, 9.0, 10.0, 0.666)
```
