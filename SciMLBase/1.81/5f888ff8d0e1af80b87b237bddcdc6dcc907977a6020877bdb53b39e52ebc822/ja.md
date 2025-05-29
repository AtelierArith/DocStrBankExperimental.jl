```julia
solve(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## キーワード引数

`solve`への引数はすべての最適化アルゴリズムで共通です。これらの共通引数は次のとおりです：

  * `maxiters`（最大反復回数）
  * `maxtime`（最適化が実行される最大時間）
  * `abstol`（目的値の変化に対する絶対許容誤差）
  * `reltol`（目的値の変化に対する相対許容誤差）
  * `callback`（コールバック関数）

選択したグローバル最適化器がローカル最適化手法を使用する場合、同様の共通ローカル最適化器引数のセットが存在します。共通ローカル最適化器引数は次のとおりです：

  * `local_method`（グローバル手法でのローカル最適化に使用される最適化器）
  * `local_maxiters`（最大反復回数）
  * `local_maxtime`（最適化が実行される最大時間）
  * `local_abstol`（目的値の変化に対する絶対許容誤差）
  * `local_reltol`（目的値の変化に対する相対許容誤差）
  * `local_options`（ローカル最適化器のキーワード引数のNamedTuple）

一部の最適化アルゴリズムには、ソルバー部分のドキュメントおよびそれぞれのドキュメントに記載された特別なキーワード引数があります。これらの引数は`kwargs...`として`solve`に渡すことができます。同様に、グローバル最適化器の`local_method`の特別なキーワード引数は、`NamedTuple`として`local_options`に渡されます。

時間が経つにつれて、共通インターフェースの下でこれらのキーワード引数のより多くをカバーすることを期待しています。

共通引数が最適化器に実装されていない場合、警告が表示されます。

## コールバック関数

コールバック関数`callback`は、各最適化ステップの後に呼び出される関数です。そのシグネチャは次のとおりです：

```julia
callback = (x,other_args) -> false
```

ここで`other_args`は最適化`f`の追加の戻り引数です。これにより、最適化から値を保存し、再計算せずにプロットや表示に使用することができます。コールバックはBoolean値を返す必要があり、デフォルトは`false`であるべきです。`true`を返すと最適化が停止します。

### コールバックの例

```julia
function loss(p)
    # いくつかの計算
    lossval,x,y,z
end

function callback(p,lossval,x,y,z)
    # いくつかの分析を行う

    # lossval < 0.01のとき、最適化を停止する
    lossval < 0.01
end
```
