```
ManualEstimator(model::SimModel; <キーワード引数>)
```

`model`（[`LinModel`](@ref) または [`NonLinModel`](@ref)）の手動状態推定器を構築します。

この [`StateEstimator`](@ref) タイプは [`PredictiveController`](@ref) オブジェクトの構築を可能にしますが、組み込みの状態推定を無効にします。ユーザーは、各時間ステップ $k$ で [`setstate!`](@ref) を通じて推定値 $\mathbf{x̂}_{k}(k)$ または $\mathbf{x̂}_{k-1}(k)$ を手動で提供する必要があります。推定器内の状態は、明らかにコントローラー内の状態と同じものを表す必要があります。これは、測定されていない外乱の決定論的および確率的モデルの両方（`nint_u` および `nint_ym` 引数）に対してです。このオブジェクトで [`preparestate!`](@ref) および [`updatestate!`](@ref) を呼び出しても、何も起こりません。使用例については拡張ヘルプを参照してください。

# 引数

  * `model::SimModel` : 推定のための（決定論的）モデル。
  * `i_ym=1:model.ny` : 測定された出力 $\mathbf{y^m}$ の `model` 出力インデックス、残りは未測定の $\mathbf{y^u}$ です。
  * `nint_u=0`: 操作入力における未測定の外乱の確率モデルのための積分器量（ベクトル）、積分器なしの場合は `nint_u=0` を使用します（拡張ヘルプを参照）。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定された出力の未測定の外乱のための `nint_u` と同じですが、積分器なしの場合は `nint_ym=0` を使用します（拡張ヘルプを参照）。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = ManualEstimator(model, nint_ym=0) # 積分器による拡張を無効にする
ManualEstimator estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 2 measured outputs ym (0 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    最初の使用例は、非線形状態推定に基づく線形予測コントローラーです。たとえば、非線形の [`MovingHorizonEstimator`](@ref) (MHE) です。`nint_u` および `nint_ym` オプションを使用したモデルの拡張スキームは、両方の [`StateEstimator`](@ref) オブジェクトに対して同一である必要があります（拡張ヘルプの [`SteadyKalmanFilter`](@ref) を参照して、拡張の詳細を確認してください）。[`ManualEstimator`](@ref) は、任意の [`PredictiveController`](@ref) オブジェクトを構築するために必要な最小限の情報を提供するラッパーとして機能します：

    ```jldoctest
    julia> function man_sim()
               f(x,u,_,_) = 0.5*sin.(x + u)
               h(x,_,_) = x
               model = NonLinModel(f, h, 10.0, 1, 1, 1, solver=nothing)
               linModel = linearize(model, x=[0], u=[0])
               man = ManualEstimator(linModel, nint_u=[1])
               mpc = LinMPC(man)
               estim = MovingHorizonEstimator(model, nint_u=[1], He=5)
               estim = setconstraint!(estim, v̂min=[-0.001], v̂max=[0.001])
               initstate!(estim, [0], [0])
               y_data, ŷ_data = zeros(5), zeros(5)
               for i=1:5
                   y = model()                     # シミュレーションされた測定
                   x̂ = preparestate!(estim, y)     # 非線形 MHE 状態推定の修正
                   ŷ = estim()                     # 非線形 MHE 推定出力
                   setstate!(mpc, x̂)               # MHE 修正状態で MPC を更新
                   u = moveinput!(mpc, [0])
                   y_data[i], ŷ_data[i] = y[1], ŷ[1]
                   updatestate!(estim, u, y)       # 非線形 MHE 推定を更新
                   updatestate!(model, u .+ 0.5)   # 負荷外乱でシミュレーターを更新
               end
               return collect([y_data ŷ_data]')
           end;

    julia> YandŶ = round.(man_sim(), digits=6)
    2×5 Matrix{Float64}:
      0.0  0.239713  0.227556  0.157837  0.098629
     -0.0  0.238713  0.226556  0.156837  0.097629
    ```

    2 番目の使用例は、ユーザーが外部ソースから計算された状態推定を手動で提供できるようにすることです。たとえば、[`LowLevelParticleFilters`](@extref LowLevelParticleFilters) のオブザーバーです。未測定の外乱のためのカスタム確率モデル（統合ホワイトノイズ以外）は、拡張された状態空間行列/関数を直接使用して [`SimModel`](@ref) オブジェクトを構築し、`nint_u=0` および `nint_ym=0` を設定することで指定できます。他の外乱モデルの例については、[`Disturbance-gallery`](@extref LowLevelParticleFilters) を参照してください。


```
