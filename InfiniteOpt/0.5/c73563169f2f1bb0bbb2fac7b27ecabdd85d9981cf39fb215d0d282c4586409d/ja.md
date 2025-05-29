```
JuMP.value(vref::GeneralVariableRef; [result::Int = 1, 
           label::Type{<:AbstractSupportLabel} = PublicLabel,
           ndarray::Bool = false, kwargs...])
```

`JuMP.value`を拡張して、最適化モデルに保存された再定式化変数に従って`vref`の値を返し、最近得られた解の結果インデックス`result`を使用します。値を要求する前に、結果が存在するかどうかを確認するには[`JuMP.has_values`](@ref JuMP.has_values(::InfiniteModel))を使用してください。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が使用する可能性のある追加の引数を示します。

デフォルトでは、公開サポートに関連付けられた値のみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限変数の値はリストとして返されます。ただし、`ndarray = true`を使用するとn次元配列を取得でき、これは変数が複数の無限パラメータ依存性を持つ場合に便利です。

結果にコンテキストを提供するために、変数の`parameter_refs`と`supports`を照会することも役立ちます。これらは値と一対一の対応関係を持ちます。また、これらの値に基づく変数を取得するために[`optimizer_model_variable`](@ref)を介して照会することも役立ちます。これらの関数は、一貫性のために同じキーワード引数で呼び出す必要があります。

拡張の場合、これは[`optimizer_model_variable`](@ref)が正しく拡張されている場合および/または変数のために[`map_value`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> value(z)
42.0
```
