```
DiscreteMeasureData(pref::GeneralVariableRef,
    coefficients::Vector{<:Real},
    supports::Vector{<:Real};
    [label::Type{<:AbstractSupportLabel} = generate_unique_label(),
    weight_function::Function = [`default_weight`](@ref),
    lower_bound::Real = NaN,
    upper_bound::Real = NaN,
    is_expect::Bool = false]
    )::DiscreteMeasureData
```

1次元の`DiscreteMeasureData`オブジェクトを返し、[`measure`](@ref)を使用して測度を定義するために利用できます。スカラー（単一）の無限パラメータの入力を受け付けます。他の引数の説明は[`DiscreteMeasureData`](@ref)のドキュメントに記載されています。supportsが範囲外であるか、supportsとcoefficientsの数が異なる場合はエラーが発生します。デフォルトでは、supportsが無限パラメータサポートストレージ内で見つけられるように、`generate_unique_label`を介してユニークな`label`が生成されます。高度な実装では、異なる動作を選択することもできますが、注意して行うべきです。

**例**

```julia-repl
julia> data = DiscreteMeasureData(pref, [0.5, 0.5], [1, 2]);
```
