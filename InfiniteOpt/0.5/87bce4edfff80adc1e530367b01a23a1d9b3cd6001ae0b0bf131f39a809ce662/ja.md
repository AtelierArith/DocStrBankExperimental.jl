```
JuMP.optimizer_index(vref::GeneralVariableRef; 
                     [label::Type{<:AbstractSupportLabel} = PublicLabel,
                     ndarray::Bool = false, kwargs...])
```

`JuMP.optimizer_index`を拡張して、最適化モデルに保存されている再定式化変数に従って、`vref`の`MathOptInterface`インデックスを返すようにします。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が使用する可能性のある追加の引数を示します。

デフォルトでは、公開サポートに関連付けられた最適化インデックスのみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限変数のインデックスはリストとして返されます。ただし、変数が複数の無限パラメータ依存性を持つ場合は、`ndarray = true`を使用してn次元配列を取得することができ、便利です。

これらのインデックスに基づく変数を取得するには、[`optimizer_model_variable`](@ref)を介してクエリすることも役立ちます。これらは一貫性のために同じキーワード引数を使用する必要があります。

拡張の場合、これは[`optimizer_model_variable`](@ref)が正しく拡張されている場合および/または変数のために[`map_optimizer_index`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> optimizer_index(x)
4-element Array{MathOptInterface.VariableIndex,1}:
 MathOptInterface.VariableIndex(2)
 MathOptInterface.VariableIndex(3)
 MathOptInterface.VariableIndex(4)
 MathOptInterface.VariableIndex(5)
```
