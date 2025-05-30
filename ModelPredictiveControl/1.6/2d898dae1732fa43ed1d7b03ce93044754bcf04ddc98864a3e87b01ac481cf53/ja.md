```
SimResult(obj::SimModel,             U_data, Y_data, D_data=[]; <keyword arguments>)
SimResult(obj::StateEstimator,       U_data, Y_data, D_data=[]; <keyword arguments>)
SimResult(obj::PredictiveController, U_data, Y_data, D_data=[]; <keyword arguments>)
```

手動で `SimResult` を構築して、`obj` シミュレーションを迅速にプロットします。

`obj` を除いて、すべての引数は `N` 列の行列である必要があります。ここで `N` は時間ステップの数です。 [`SimResult`](@ref) オブジェクトは、シミュレーション結果を迅速にプロットすることを可能にします。単にそれらに対して `plot` を呼び出すだけです。

# 引数

!!! info
    *`強調`* されたキーワード引数は、非Unicodeの代替手段です。


  * `obj` : シミュレーションされた [`SimModel`](@ref)/[`StateEstimator`](@ref)/[`PredictiveController`](@ref)
  * `U_data` : 操作された入力
  * `Y_data` : プラント出力
  * `D_data=[]` : 測定された外乱
  * `X_data=nothing` : プラント状態
  * `X̂_data=nothing` または *`Xhat_data`* : 推定された状態
  * `Ŷ_data=nothing` または *`Yhat_data`* : 推定された出力
  * `Ry_data=nothing` : プラント出力セットポイント
  * `Ru_data=nothing` : 操作された入力セットポイント
  * `plant=get_model(obj)` : シミュレーションされたプラントモデル、デフォルトは `obj` 内部のプラントモデル

# 例

```jldoctest
julia> model = LinModel(tf(1, [1, 1]), 1.0);

julia> N = 5; U_data = fill(1.0, 1, N); Y_data = zeros(1, N);

julia> for i=1:N; updatestate!(model, U_data[:, i]); Y_data[:, i] = model(); end; Y_data
1×5 Matrix{Float64}:
 0.632121  0.864665  0.950213  0.981684  0.993262

julia> res = SimResult(model, U_data, Y_data)
Simulation results of LinModel with 5 time steps.
```
