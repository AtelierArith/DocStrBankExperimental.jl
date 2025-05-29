```
FunctionalDiscreteMeasureData(prefs::AbstractArray{GeneralVariableRef},
    coeff_func::Function,
    min_num_supports::Int,
    label::Type{<:AbstractSupportLabel};
    [weight_function::Function = [`default_weight`](@ref),
    lower_bounds::AbstractArray{<:Real} = [NaN...],
    upper_bounds::AbstractArray{<:Real} = [NaN...],
    is_expect::Bool = false]
    )::FunctionalDiscreteMeasureData
```

多次元の `FunctionalDiscreteMeasureData` オブジェクトを返し、[`measure`](@ref) を使用して測度を定義するために利用できます。これは無限のパラメータの配列の入力を受け付けます。他の引数の説明は [`FunctionalDiscreteMeasureData`](@ref) のドキュメントに記載されています。`prefs` が無限のパラメータでない場合や混合パラメータタイプが提供された場合にエラーが発生します。`label` の組み込みの選択肢には以下が含まれます：

  * `All`: `prefs` に保存されているすべてのサポートを使用
  * `MCSample`: `prefs` に関連付けられたモンテカルロサンプルを使用
  * `WeightedSample`: `prefs` に関連付けられた重み付きモンテカルロサンプルを使用
  * `UniformGrid`: `prefs` に関連付けられた均一グリッドポイントを使用。

**例**

```julia-repl
julia> data = FunctionalDiscreteMeasureData(prefs, my_func, 20, MCSample);
```
