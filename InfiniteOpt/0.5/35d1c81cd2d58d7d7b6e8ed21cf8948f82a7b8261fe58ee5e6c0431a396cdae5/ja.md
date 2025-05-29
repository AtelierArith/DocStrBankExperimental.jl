```
FunctionalDiscreteMeasureData(pref::GeneralVariableRef,
    coeff_func::Function,
    min_num_supports::Int,
    label::Type{<:AbstractSupportLabel};
    [weight_function::Function = [`default_weight`](@ref),
    lower_bound::Real = NaN,
    upper_bound::Real = NaN,
    is_expect::Bool = false,
    generative_support_info::AbstractGenerativeInfo = NoGenerativeSupports()]
    )::FunctionalDiscreteMeasureData
```

1次元の`FunctionalDiscreteMeasureData`オブジェクトを返し、[`measure`](@ref)を使用して測度を定義するために利用できます。スカラー（単一）無限パラメータの入力を受け付けます。他の引数の説明は[`FunctionalDiscreteMeasureData`](@ref)のドキュメントに記載されています。`pref`が無限パラメータでない場合はエラーになります。`label`の組み込み選択肢には以下が含まれます：

  * `All`: `pref`に保存されているすべてのサポートを使用
  * `MCSample`: `pref`に関連付けられたモンテカルロサンプルを使用
  * `WeightedSample`: `pref`に関連付けられた重み付きモンテカルロサンプルを使用
  * `UniformGrid`: `pref`に関連付けられた均一グリッドポイントを使用。

**例**

```julia-repl
julia> data = FunctionalDiscreteMeasureData(pref, my_func, 20, UniformGrid);
```
