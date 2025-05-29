```
add_supports_to_parameters(data::AbstractMeasureData)::Nothing
```

`data`を使用して、基盤となる無限パラメータに適切なサポートを追加します。これは[`add_measure`](@ref)によって内部的に使用されるメソッドであり、ユーザー定義の測定データ型に対して定義されるべきです。
