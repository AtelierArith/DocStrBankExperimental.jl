```
JuMP.shadow_price(cref::InfOptConstraintRef; 
                  [label::Type{<:AbstractSupportLabel} = PublicLabel,
                  ndarray::Bool = false, kwargs...])
```

`JuMP.shadow_price`を拡張して、最適化モデルに保存されている再定式化制約に従って`cref`のシャドウ価格を返します。結果が存在するかどうかを確認するには、シャドウ価格を要求する前に[`JuMP.has_duals`](@ref JuMP.has_duals(::InfiniteModel))を使用してください（それは双対を使用します）。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するもので、`kwargs`はユーザー拡張が使用する可能性のある追加の引数を示します。

デフォルトでは、公開サポートに関連するシャドウ価格のみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限制約の価格はリストとして返されます。ただし、`ndarray = true`を使用するとn次元配列を取得でき、これは制約が複数の無限パラメータ依存性を持つ場合に便利です。

これらのシャドウ価格に基づく制約を取得するには、[`optimizer_model_constraint`](@ref)を介してクエリすることも役立ちます。`parameter_refs`や`supports`を呼び出すことも洞察を与えるかもしれません。一貫性のために同じキーワード引数を使用することを忘れないでください。

拡張の場合、これは[`optimizer_model_constraint`](@ref)が正しく拡張されている場合および/または制約のために[`map_dual`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> shadow_price(c1)
4-element Array{Float64,1}:
 42.0
 42.0
 -32.3
 -0.0
```
