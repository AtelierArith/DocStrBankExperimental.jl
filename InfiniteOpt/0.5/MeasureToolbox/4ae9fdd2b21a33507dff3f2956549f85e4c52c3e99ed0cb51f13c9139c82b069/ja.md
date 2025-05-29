```
integral(expr::JuMP.AbstractJuMPScalar,
         pref::GeneralVariableRef,
         [lower_bound::Real = lower_bound(pref),
         upper_bound::Real = upper_bound(pref);
         kwargs...])::GeneralVariableRef
```

`expr`の積分を無限パラメータ`pref`に関して`lower_bound`から`upper_bound`まで評価する測度参照を返します。これは、次の形式の積分を考慮します: $\int_{p \in P} expr(p) w(p) dp$ ここで、$p$は無限パラメータであり、$w$はデフォルトで1の重み関数です。この関数は、高レベルのインターフェースを提供し、最終的にキーワード引数`eval_method`に従って[`generate_integral_data`](@ref)を介して[`AbstractMeasureData`](@ref)の適切な具体的形式を構築します。これは[`measure`](@ref)と共に使用されます。`expr`が単一の変数参照でない場合は、[`@integral`](@ref)を呼び出すことが推奨されます。無効な境界入力に対するエラーがあります。

キーワード引数は次のとおりです:

  * `eval_method::AbstractUnivariateMethod`: 数値評価スキームを決定するために使用されます。可能な選択肢には以下が含まれます:

      * [`Automatic()`](@ref MeasureToolbox.Automatic)
      * [`UniTrapezoid()`](@ref MeasureToolbox.UniTrapezoid)
      * [`UniMCSampling()`](@ref MeasureToolbox.UniMCSampling)
      * [`UniIndepMCSampling()`](@ref MeasureToolbox.UniIndepMCSampling)
      * [`Quadrature()`](@ref MeasureToolbox.Quadrature)
      * [`GaussHermite()`](@ref MeasureToolbox.GaussHermite)
      * [`GaussLegendre()`](@ref MeasureToolbox.GaussLegendre)
      * [`FEGaussLobatto()`](@ref MeasureToolbox.FEGaussLobatto)
      * [`GaussLageurre()`](@ref MeasureToolbox.GaussLaguerre)
      * [`GaussLobatto()`](@ref MeasureToolbox.GaussLobatto)
      * [`GaussChebyshev(order)`](@ref MeasureToolbox.GaussChebyshev)
      * [`GaussRadau()`](@ref MeasureToolbox.GaussRadau)
      * [`GaussJacobi(α, β)`](@ref MeasureToolbox.GaussJacobi)
  * `num_supports`: 生成されるサポートの最小数（`eval_method`によって使用される場合）
  * `weight_func`: 上記の$w(p)$で、パラメータ値入力とスカラー出力を持ちます

すべての1次元積分呼び出しのデフォルトキーワード引数値を更新するには、[`set_uni_integral_defaults`](@ref)を参照してください。

**例**

```julia-repl
julia> @infinite_parameter(model, x in [0, 1])
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> int = integral(f, x)
∫{x ∈ [0, 1]}[f(x)]

julia> expand(int)
0.2 f(0.8236475079774124) + 0.2 f(0.9103565379264364) + 0.2 f(0.16456579813368521) + 0.2 f(0.17732884646626457) + 0.2 f(0.278880109331201)
```
