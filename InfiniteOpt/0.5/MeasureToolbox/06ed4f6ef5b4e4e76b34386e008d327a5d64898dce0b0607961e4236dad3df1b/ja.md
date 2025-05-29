```
integral(expr::JuMP.AbstractJuMPScalar,
         prefs::AbstractArray{GeneralVariableRef},
         [lower_bounds::Union{Real, AbstractArray{<:Real}} = [lower_bound(pref)...],
         upper_bounds::Union{Real, AbstractArray{<:Real}} = [upper_bound(pref)...];
         kwargs...])::GeneralVariableRef
```

`expr`に関して、無限のパラメータ`prefs`の範囲を`lower_bounds`から`upper_bounds`まで評価する測度参照を返します。これは、次の形式の積分を考慮します: $\int_{p \in P} expr(p) w(p) dp$ ここで、$p$は無限のパラメータであり、$w$はデフォルトで1の重み関数です。この関数は、最終的にキーワード引数`eval_method`に従って[`generate_integral_data`](@ref)を介して適切な具体的な[`AbstractMeasureData`](@ref)の形を構築する高レベルのインターフェースを提供します。その後、[`measure`](@ref)と共に使用されます。`expr`が単一の変数参照でない場合は、[`@integral`](@ref)を呼び出すことが推奨されます。コンテナの型と次元が一致しない場合や、境界が無効な場合にエラーが発生します。

キーワード引数は次のとおりです:

  * `eval_method::AbstractMultivariateMethod`: 数値評価スキームを決定するために使用されます。可能な選択肢には次が含まれます:

      * [`Automatic()`](@ref MeasureToolbox.Automatic)
      * [`MultiMCSampling()`](@ref MeasureToolbox.MultiMCSampling)
      * [`MultiIndepMCSampling()`](@ref MeasureToolbox.MultiIndepMCSampling)
  * `num_supports`: 生成されるサポートの最小数（`eval_method`で使用される場合）
  * `weight_func`: 上記の$w(p)$で、パラメータ値入力とスカラー出力を持ちます

すべての多次元積分呼び出しのデフォルトのキーワード引数値を更新するには、[`set_multi_integral_defaults`](@ref)を参照してください。

**例**

```julia-repl
julia> @infinite_parameter(model, x[1:2] in [0, 1], independent = true);

julia> @variable(model, f, Infinite(x));

julia> int = integral(f, x)
∫{x ∈ [0, 1]^2}[f(x)]
```
