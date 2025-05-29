```
SteadyStateSolver(method::Symbol; kwargs...)
```

定常状態ソルバーオプション（`method`、`tolerances`など）を使用して定常状態を計算します。ここで、ODEの右辺`f`は`du = f(u, p, t) ≈ 0`を満たします。

定常状態は2つの方法で計算できます。`method=:Simulate`の場合、ODEモデルをシミュレーションして`du = f(u, p, t) ≈ 0`になるまで進めます。この際、提供された`ODESolver`のオプションを`PEtabODEProblem`に定義します。このアプローチは**強く**推奨されます。`method=:Rootfinding`の場合、非線形ソルバーのアルゴリズムを使用してRHS`f(u, p, t) = 0`の根を直接見つけます。根を見つけるアプローチは、シミュレーションアプローチよりも信頼性が低いです（以下の説明を参照）。

## キーワード引数

  * `termination_check = :wrms`: `method = :Simulate`の場合にモデルが定常状態に達したかどうかを確認するアプローチ。2つのアプローチがサポートされています：

      * `:wrms`: 加重平均二乗根。終了条件は次の通りです：$\sqrt{\frac{1}{N} \sum_i^N \Big( \frac{du_i}{reltol * u_i + abstol}\Big)^2} < 1$
      * `:Newton`: ニュートン法のステップ`Δu`が十分に小さい場合に終了します：$\sqrt{\frac{1}{N} \sum_i^N \Big(\frac{\Delta u_i}{reltol * u_i + abstol}\Big)^2} < 1$ `:Newton`アプローチは、ODEモデルのRHSのヤコビアンが可逆である場合にのみ計算可能なニュートンステップ`Δu`を必要とします。これが満たされない場合、`pseudoinverse = true`であれば擬似逆行列が使用され、それ以外の場合は`wrms`が使用されます。`:Newton`の終了条件はODEのスケールを考慮するため、`:wrms`よりもパフォーマンスが良いはずですが、ベンチマークがこれを確認するまで、`:wrms`を推奨します。
  * `pseudoinverse = true`: ヤコビアンの逆行列の計算が失敗した場合に擬似逆行列を使用するかどうか。
  * `rootfinding_alg = nothing`: `method = :Rootfinding`の場合に使用するNonlinearSolve.jlの根探索アルゴリズム。空のままにすると、デフォルトのNonlinearSolve.jlアルゴリズムが使用されます。
  * `abstol`: NonlinearSolve.jlの根探索問題または`termination_check`の式に対する絶対許容誤差。デフォルトは`100 * abstol_ode`で、ここで`abstol_ode`は`PEtabODEProblem`の`ODESolver`に対する許容誤差です。
  * `reltol`: NonlinearSolve.jlの根探索問題または`termination_check`の式に対する相対許容誤差。デフォルトは`100 * reltol_ode`で、ここで`reltol_ode`は`PEtabODEProblem`の`ODESolver`に対する許容誤差です。
  * `maxiters`: `method = :Rootfinding`の場合に使用する最大反復回数。

## 説明

次の形式のODEモデルについて：

$$
\frac{\mathrm{d}u}{\mathrm{d}t} = du = f(u, p, t)
$$

定常状態は次のように定義されます：

$$
f(u, p, t) = 0.0
$$

定常状態は、初期値`u₀`のセットからODEモデルをシミュレーションして`du ≈ 0`になるまで進めるか、[ニュートン法](https://en.wikipedia.org/wiki/Newton%27s_method)のような根探索アルゴリズムを使用して`f(u, p, t) = 0.0`を直接解くことによって計算できます。根探索アプローチは計算効率が高いですが（ODE全体を解く必要がないため）、信頼性が低く、誤った根に収束する可能性があります。たとえば、正の初期値を持つ質量作用モデルでは、実行可能な根は`u`で正であるべきです。これは、シミュレーションを通じて定常状態を計算する際には一般的に満たされます（負の根は通常ODEソルバーが失敗した場合にのみ発生します）。しかし、根探索ではそのような保証はなく、`f(u, p, t) = 0.0`を満たす任意の根が返される可能性があります。これに一致して、ベンチマークはシミュレーションが最も信頼性の高い方法であることを示しています[1]。

別の選択肢は、定常状態を象徴的に解くことです。可能であれば、これが最も計算効率の良いアプローチです[1]。

1. Fiedler et al, BMC system biology, pp 1-19 (2016)

```
