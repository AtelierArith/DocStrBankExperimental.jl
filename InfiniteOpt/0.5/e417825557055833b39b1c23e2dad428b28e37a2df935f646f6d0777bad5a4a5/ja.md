```
JuMP.value(expr::JuMP.AbstractJuMPScalar; [result::Int = 1, 
           label::Type{<:AbstractSupportLabel} = PublicLabel,
           ndarray::Bool = false, kwargs...])
```

最適化された変数値に基づいて、最近得られた解の結果インデックス `result` に従って `expr` の値を返します。値を要求する前に、結果が存在するかどうかを確認するには [`JuMP.has_values`](@ref JuMP.has_values(::InfiniteModel)) を使用してください。

キーワード引数 `label` と `ndarray` は `TranscriptionOpt` が使用するものであり、`kwargs` はユーザー拡張が使用する追加のものを示します。

デフォルトでは、公開サポートに関連付けられた値のみが返され、全セットには `label = All` を介してアクセスできます。さらに、無限表現の値はリストとして返されます。ただし、`ndarray = true` を指定することで n 次元配列を取得でき、これは表現が複数の無限パラメータ依存性を持つ場合に便利です。

結果に文脈を提供するために、表現の `parameter_refs` と `supports` を照会することも役立ちます。これらは値と一対一の対応関係を持ちます。また、これらの値に基づく表現を取得するには [`optimizer_model_expression`](@ref) を介して照会することも役立ちます。これらは一貫性のために同じキーワード引数を使用する必要があります。

拡張の場合、これは [`optimizer_model_expression`](@ref) が正しく拡張されている場合および/または [`map_value`](@ref) が表現のために拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> value(my_finite_expr)
23.34

julia> value(my_infinite_expr)
4-element Array{Float64,1}:
 -0.0
 20.9
 20.9
 20.9
```
