```
JuMP.dual(cref::InfOptConstraintRef; [result::Int = 1, 
          label::Type{<:AbstractSupportLabel} = PublicLabel,
          ndarray::Bool = false, kwargs...])
```

`JuMP.dual`を拡張して、最適化モデルに保存された再定式化制約に従って`cref`の双対を、最近得られた解の結果インデックス`result`と共に返します。結果が存在するかどうかを確認するには、[`JuMP.has_duals`](@ref JuMP.has_duals(::InfiniteModel))を使用してください。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が使用する追加の引数を示します。

デフォルトでは、公開サポートに関連する双対のみが返され、全セットは`label = All`を介してアクセスできます。さらに、無限制約の双対はリストとして返されます。ただし、制約が複数の無限パラメータ依存性を持つ場合、`ndarray = true`を使用することでn次元配列を取得できます。

これらの双対に基づく制約を取得するには、[`optimizer_model_constraint`](@ref)を介してクエリを行うことも役立ちます。`parameter_refs`や`supports`を呼び出すことも洞察を与えるかもしれません。一貫性のために同じキーワード引数を使用することを忘れないでください。

拡張の場合、これは[`optimizer_model_constraint`](@ref)が正しく拡張されている場合および/または制約のために[`map_dual`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> dual(c1)
4-element Array{Float64,1}:
 -42.0
 -42.0
 32.3
 0.0
```
