```
generate_integral_data(
    prefs::Union{InfiniteOpt.GeneralVariableRef, Vector{InfiniteOpt.GeneralVariableRef}},
    lower_bounds::Union{Real, Vector{<:Real}},
    upper_bounds::Union{Real, Vector{<:Real}},
    method::V; [num_supports::Int = InfiniteOpt.DefaultNumSupports,
    weight_func::Function = InfiniteOpt.default_weight,
    extra_kwargs...]
    )::InfiniteOpt.AbstractMeasureData where {V <: AbstractIntegralMethod}
```

`AbstractMeasureData`の適切な具体的実現を`method`を使用して生成します。ここで、`prefs`、`lower_bounds`、および`upper_bounds`は、`integral`から呼び出されるときに常に1対1の対応関係を持ちます。それぞれの説明については、メソッドのドキュメント文字列を参照してください。

ユーザー定義のメソッド拡張は、最初に`AbstractUnivariateMethod`または`AbstractMultivariateMethod`から継承する具体的な`method`タイプを定義し、その後、そのタイプを使用して`method`を拡張する必要があります。
