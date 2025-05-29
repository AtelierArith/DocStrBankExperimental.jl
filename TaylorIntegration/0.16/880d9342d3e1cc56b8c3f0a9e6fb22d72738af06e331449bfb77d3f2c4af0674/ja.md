```
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, t0, tmax, order, abstol, params[=nothing]; kwargs... )
taylorinteg(f, g, x0, trange, order, abstol, params[=nothing]; kwargs... )
```

`taylorinteg`の根探索法。

関数 `g(dx, x, params, t)::Tuple{Bool, Taylor1{T}}`（イベント関数と呼ばれる）を与えると、`taylorinteg`は、`cond1::Bool`が満たされている場合（`true`）、`cond2 == 0`（`cond2::Taylor1{T}`）で定義された根またはイベントの発生をチェックします。したがって、`g`はタプル (cond1, cond2) を返すと仮定されます。次に、`taylorinteg`はニュートン-ラフソン法を実行することによってその根（またはイベント、または交差）を見つけようとします。`eventorder=n`キーワード引数を指定して呼び出すと、`taylorinteg`は自動微分を介して計算される`cond2`の`n`-次導関数の根を検索します。

現在のキーワード引数は次のとおりです：

  * `maxsteps[=500]`: 最大統合ステップ数。
  * `parse_eqs[=true]`: [`@taylorize`](@ref)で作成された`jetcoeffs!`の専門的なメソッドを使用します。
  * `eventorder[=0]`: 根が計算される`g`の導関数の順序。
  * `newtoniter[=10]`: 検出された根ごとの最大ニュートン-ラフソン反復回数。
  * `nrabstol[=eps(T)]`: ニュートン-ラフソン法の許容誤差；Tは`t0`、`tmax`（または`eltype(trange)`）および`abstol`の共通型です。
  * `dense[=true]`: 各時間ステップでのテイラー多項式展開を出力します。

## 例：

```julia
using TaylorIntegration

function pendulum!(dx, x, params, t)
    dx[1] = x[2]
    dx[2] = -sin(x[1])
    nothing
end

g(dx, x, params, t) = (true, x[2])

x0 = [1.3, 0.0]

# 解に沿った`g`の根を見つける
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20)

# 解に沿った`g`の2次導関数の根を見つける
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20; eventorder=2)

# 密な解出力で解に沿った`g`の根を見つける
sol = taylorinteg(pendulum!, g, x0, 0.0, 22.0, 28, 1.0E-20, dense=true)

# 解が返される時間
tv = 0.0:1.0:22.0

# 解に沿った`g`の根を見つける；`tv`の各値でのみ解を返す
sol = taylorinteg(pendulum!, g, x0, tv, 28, 1.0E-20)

# 解に沿った`g`の2次導関数の根を見つける；`tv`の各値でのみ解を返す
sol = taylorinteg(pendulum!, g, x0, tv, 28, 1.0E-20; eventorder=2)
```
