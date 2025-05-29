```
sol = forward_trajectory(kf::AbstractKalmanFilter, u::Vector, y::Vector, p=parameters(kf); debug=false)
```

カーマンフィルタを前方に実行して、全体の軌道 `u, y` に沿って（オフライン / バッチ）フィルタリングを行います。

次の内容を持つ `KalmanFilteringSolution` を返します：

  * `x`: 予測 $x(t|t-1)$
  * `xt`: フィルタリングされた推定値 $x(t|t)$
  * `R`: 予測共分散行列 $R(t|t-1)$
  * `Rt`: フィルタ共分散 $R(t|t)$
  * `ll`: 対数尤度

`sol` はプロットできます。

```
plot(sol::KalmanFilteringSolution; plotx = true, plotxt=true, plotu=true, ploty=true)
```

詳細については [`KalmanFilteringSolution`](@ref) を参照してください。

# 拡張ヘルプ

## 非常に大きなシステム

システムが非常に大きい場合、すなわち状態の次元が非常に大きく、配列 `u,y` が長い場合、この関数はすべての共分散行列 `R, Rt` を保存するために多くのメモリを使用する可能性があります。この関数によって保持されるすべての情報が必要ない場合は、次の関数のいずれかを呼び出すことを選択できます。

  * [`loglik`](@ref)
  * [`LowLevelParticleFilters.sse`](@ref)
  * [`LowLevelParticleFilters.prediction_errors!`](@ref)

これらは、はるかに少ない情報を保存します。これらの関数によって実行される計算量は同じですが、保存される内容と返される内容に違いがあります。

## コールバック

条件付きリセットや適応共分散の実装などの高度な使用法のために、コールバック関数を利用できます。

  * `pre_correct_cb(kf, u, y, p, t)`: 修正ステップの前に呼び出され、`nothing` または修正ステップで使用する共分散行列 `R2` を返します。
  * `pre_predict_cb(kf, u, y, p, t, ll, e, S, Sᵪ)`: 予測ステップの前に呼び出され、`nothing` または予測ステップで使用する共分散行列 `R1` を返します。このコールバックの引数は `filter, input, measurement, parameters, time, loglikelihood, prediction error, innovation covariance and Cholesky factor of the innovation covariance` であり、基本的に修正ステップ後に利用可能なすべての情報です。

フィルタループは、次のステップで構成されます。この順序で：

1. `pre_correct_cb`
2. `correct!`
3. `pre_predict_cb`
4. `predict!`

```
