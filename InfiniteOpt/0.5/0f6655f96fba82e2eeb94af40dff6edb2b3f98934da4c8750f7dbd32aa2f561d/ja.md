```
JuMP.value(cref::InfOptConstraintRef; [result::Int = 1,
           label::Type{<:AbstractSupportLabel} = PublicLabel,
           ndarray::Bool = false, kwargs...])
```

`JuMP.value`を拡張して、最適化モデルに保存された再定式化制約に従って`cref`の値を返し、最近得られた解の結果インデックス`result`を使用します。値を要求する前に、結果が存在するかどうかを確認するには、[`JuMP.has_values`](@ref JuMP.has_values(::InfiniteModel))を使用してください。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が使用する可能性のある追加の引数を示します。

デフォルトでは、公開サポートに関連付けられた値のみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限制約の値はリストとして返されます。ただし、制約が複数の無限パラメータ依存性を持つ場合、`ndarray = true`を使用することでn次元配列を取得できます。

結果にコンテキストを提供するために、制約の`parameter_refs`と`supports`を照会することも役立ちます。これらは値と一対一の対応関係を持ちます。また、これらの値に基づく制約を取得するには、[`optimizer_model_constraint`](@ref)を介して照会することも役立ちます。デフォルトでは、公開サポートに対応する値のみが返されます。これらの関数は、一貫性のために同じキーワード引数で呼び出す必要があります。

拡張の場合、これは[`optimizer_model_constraint`](@ref)が正しく拡張されている場合および/または制約のために[`map_value`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> value(c1)
4-element Array{Float64,1}:
 -0.0
 20.9
 20.9
 20.9
```
