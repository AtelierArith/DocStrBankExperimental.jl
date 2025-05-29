```
PhysicsInformedNN(chain, strategy; init_params = nothing, phi = nothing,
                  param_estim = false, additional_loss = nothing,
                  adaptive_loss = nothing, logger = nothing, log_options = LogOptions(),
                  iteration = nothing, kwargs...)
```

`PDESystem`インターフェースのための`discretize`アルゴリズムで、Physics-Informed Neural Networks (PINN)手法を使用して`PDESystem`を`OptimizationProblem`に変換します。

## 位置引数

  * `chain`: d次元の入力と1次元の出力を持つLux/Fluxチェーンのベクトルで、各従属変数に対応します。この仕様は、PDESystemで指定された従属変数の順序を尊重します。Fluxチェーンは、内部で`adapt(FromFluxAdaptor(), chain)`を使用してLuxに変換されます。
  * `strategy`: 使用されるトレーニング戦略を決定します。詳細については、トレーニング戦略のドキュメントを参照してください。

## キーワード引数

  * `init_params`: ニューラルネットワークの初期パラメータ。`init_params`が指定されていない場合、ニューラルネットワークのデフォルトパラメータが使用されます。Luxの場合、デフォルトはFloat64に変換されます。
  * `phi`: 試行解で、`phi(x,p)`として指定され、`x`は従属変数の座標ベクトル、`p`はphi関数の重み（一般的には`phi`を定義するニューラルネットワークの重み）です。デフォルトでは、これは`chain`から生成されます。これは、トレーニング問題に機能情報をより直接的に課すためにのみ使用されるべきで、例えばテスト関数の定式化によって境界条件を課すことができます。
  * `adaptive_loss`: 適応損失関数の選択。詳細については[adaptive loss page](@ref adaptive_loss)を参照してください。デフォルトでは適応性はありません。
  * `additional_loss`: 関数`additional_loss(phi, θ, p_)`で、`phi`はニューラルネットワークの試行解、`θ`はニューラルネットワークの重み、`p_`は`OptimizationProblem`のハイパーパラメータです。`param_estim = true`の場合、`θ`にはベクトルの末尾に追加された微分方程式のパラメータも含まれます。
  * `param_estim`: 微分方程式のパラメータを`additional_loss`関数に送信する値に含めるべきかどうか。デフォルトは`false`です。
  * `logger`: ?? ドキュメントが必要
  * `log_options`: ?? これはなぜロガーとは別なのか？
  * `iteration`: イテーションカウンタを制御するために使用されます???
  * `kwargs`: `solve`で`OptimizationProblem`にスプラットされる追加のキーワード引数。
