```julia
solve(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## キーワード引数

`solve`への引数は、すべての最適化アルゴリズムで共通です。これらの共通引数は次のとおりです。

  * `maxiters`（最大反復回数）
  * `maxtime`（最適化が実行される最大時間）
  * `abstol`（目的値の変化に対する絶対許容誤差）
  * `reltol`（目的値の変化に対する相対許容誤差）
  * `callback`（コールバック関数）

選択したグローバル最適化アルゴリズムがローカル最適化手法を使用する場合、同様の共通ローカル最適化引数のセットがあります。共通ローカル最適化引数は次のとおりです。

  * `local_method`（グローバル手法でのローカル最適化に使用される最適化アルゴリズム）
  * `local_maxiters`（最大反復回数）
  * `local_maxtime`（最適化が実行される最大時間）
  * `local_abstol`（目的値の変化に対する絶対許容誤差）
  * `local_reltol`（目的値の変化に対する相対許容誤差）
  * `local_options`（ローカル最適化アルゴリズムのキーワード引数のNamedTuple）

一部の最適化アルゴリズムには、ドキュメントのソルバー部分およびそれぞれのドキュメントに記載された特別なキーワード引数があります。これらの引数は、`kwargs...`として`solve`に渡すことができます。同様に、グローバル最適化アルゴリズムの`local_method`の特別なキーワード引数は、`local_options`にNamedTupleとして渡されます。

時間が経つにつれて、これらのキーワード引数のより多くを共通インターフェースの下でカバーできることを期待しています。

共通引数が最適化アルゴリズムに実装されていない場合、警告が表示されます。

## コールバック関数

コールバック関数`callback`は、すべての最適化ステップの後に呼び出される関数です。そのシグネチャは次のとおりです。

```julia
callback = (u, loss_val, other_args) -> false
```

ここで、`u`と`loss_val`は最適化ループ内の現在の最適化変数と損失/目的値であり、`other_args`は最適化`f`から返される追加のものです。これにより、最適化からの値を保存し、再計算せずにプロットや表示に使用することができます。コールバックはBoolean値を返す必要があり、デフォルトは`false`で、`true`を返すと最適化が停止します。

### コールバックの例

ここでは、最適化変数の現在の値で予測をプロットするコールバック関数の例を示します。ここでの損失関数は損失と予測、すなわち`ODEProblem` `prob`の解を返すため、コールバック内で予測を使用できます。

```julia
function predict(u)
    Array(solve(prob, Tsit5(), p = u))
end

function loss(u, p)
    pred = predict(u)
    sum(abs2, batch .- pred), pred
end

callback = function (p, l, pred; doplot = false) #トレーニングを観察するためのコールバック関数
    display(l)
    # データに対する現在の予測をプロット
    if doplot
        pl = scatter(t, ode_data[1, :], label = "data")
        scatter!(pl, t, pred[1, :], label = "prediction")
        display(plot(pl))
    end
    return false
end
```
