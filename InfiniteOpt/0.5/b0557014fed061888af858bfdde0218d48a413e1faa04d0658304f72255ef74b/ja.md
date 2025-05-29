```
DiscreteMeasureData(prefs::AbstractArray{GeneralVariableRef},
    coefficients::Vector{<:Real},
    supports::Vector{<:AbstractArray{<:Real}};
    label::Type{<:AbstractSupportLabel} = generate_unique_label(),
    weight_function::Function = [`default_weight`](@ref),
    lower_bounds::AbstractArray{<:Real} = [NaN...],
    upper_bounds::AbstractArray{<:Real} = [NaN...],
    is_expect::Bool = false
    )::DiscreteMeasureData
```

`DiscreteMeasureData`オブジェクトを返し、[`measure`](@ref)を使用して測度を定義するために利用できます。これは配列（多）パラメータの入力を受け入れます。supportsベクター内の内部配列は、`parameter_refs`に使用される配列のフォーマットと一致する必要があります。他の引数の説明は、[`DiscreteMeasureData`](@ref)のドキュメントに記載されています。supportsが範囲外の場合、supportsとcoefficientsの数が不均等な場合、配列フォーマットが一致しない場合、または混合無限パラメータタイプが与えられた場合にエラーが発生します。デフォルトでは、supportsが無限パラメータサポートストレージに位置できるように、`generate_unique_label`を介して一意の`label`が生成されます。高度な実装では、異なる動作を選択することができますが、注意して行うべきです。

**例**

```julia-repl
julia> data = DiscreteMeasureData(prefs, [0.5, 0.5], [[1, 1], [2, 2]]);
```
