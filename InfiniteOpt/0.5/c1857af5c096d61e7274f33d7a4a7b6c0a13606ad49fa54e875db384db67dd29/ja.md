```
JuMP.upper_bound(data::AbstractMeasureData)::Union{Float64, Vector{Float64}}
```

`data` に関連付けられた下限を返します。これはそのドメインを定義します。これは内部メソッドとして意図されていますが、拡張に役立つ場合があります。ユーザー定義の測定データ型は、必要に応じてこの関数を拡張するべきですが、そうでない場合は `NaN` が返されます。
