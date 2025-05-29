```julia
solve(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## キーワード引数

`solve`への引数は、すべての最適化アルゴリズムで共通です。これらの共通引数は次のとおりです。

  * `maxiters`: 最大反復回数
  * `maxtime`: 最適化が実行される最大時間（通常は秒単位）
  * `abstol`: 目的値の変化に対する絶対許容誤差
  * `reltol`: 目的値の変化に対する相対許容誤差
  * `callback`: コールバック関数

一部の最適化アルゴリズムには、ドキュメントのソルバー部分およびそれぞれのドキュメントに記載された特別なキーワード引数があります。これらの引数は、`kwargs...`として`solve`に渡すことができます。同様に、グローバル最適化の`local_method`の特別なキーワード引数は、`NamedTuple`として`local_options`に渡されます。

時間が経つにつれて、共通インターフェースの下でこれらのキーワード引数のより多くをカバーすることを期待しています。

共通引数が最適化アルゴリズムに実装されていない場合、警告が表示されます。

## コールバック関数

コールバック関数`callback`は、各最適化ステップの後に呼び出される関数です。そのシグネチャは次のとおりです。

```julia
callback = (state, loss_val) -> false
```

ここで、`state`は`OptimizationState`であり、ソルバーの現在の反復に関する情報を格納し、`loss_val`は損失/目的値です。`state`のフィールドに関する詳細は、`OptimizationState`のドキュメントを参照してください。コールバックはBoolean値を返す必要があり、デフォルトは`false`であるため、`true`を返すと最適化が停止します。

### コールバックの例

ここでは、最適化変数の現在の値で予測をプロットするコールバック関数の例を示します。可視化コールバックには、現在のパラメータ、すなわち`ODEProblem` `prob`の解における予測が必要です。したがって、コールバック内で再度`predict`関数を呼び出します。

```julia
function predict(u)
    Array(solve(prob, Tsit5(), p = u))
end

function loss(u, p)
    pred = predict(u)
    sum(abs2, batch .- pred)
end

callback = function (state, l; doplot = false) #トレーニングを観察するためのコールバック関数
    display(l)
    # データに対する現在の予測をプロット
    if doplot
        pred = predict(state.u)
        pl = scatter(t, ode_data[1, :], label = "data")
        scatter!(pl, t, pred[1, :], label = "prediction")
        display(plot(pl))
    end
    return false
end
```

選択した方法がローカル最適化手法を使用するグローバル最適化アルゴリズムである場合、共通のローカル最適化引数のセットが存在します。例として`MLSL`または`AUGLAG`をNLoptから参照してください。共通のローカル最適化引数は次のとおりです。

  * `local_method`: グローバルメソッドでのローカル最適化に使用される最適化アルゴリズム
  * `local_maxiters`: 最大反復回数
  * `local_maxtime`: 最適化が実行される最大時間（秒単位）
  * `local_abstol`: 目的値の変化に対する絶対許容誤差
  * `local_reltol`: 目的値の変化に対する相対許容誤差
  * `local_options`: ローカル最適化アルゴリズムのキーワード引数の`NamedTuple`
