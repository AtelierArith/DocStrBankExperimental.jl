```
generate_expect_data(domain::AbstractInfiniteDomain, 
                     prefs::Union{GeneralVariableRef, Vector{GeneralVariableRef}}, 
                     num_supports::Int; 
                     [kwargs...])::AbstractMeasureData
```

`domain` と無限パラメータ `prefs` に基づいて、`AbstractMeasureData` の具体的なインスタンスを生成します。これは内部メソッドとして意図されていますが、ユーザー定義の無限ドメインタイプに対して拡張されるべきです。
