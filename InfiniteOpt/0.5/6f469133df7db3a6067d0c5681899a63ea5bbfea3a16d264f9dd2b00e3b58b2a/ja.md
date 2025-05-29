```
JuMP.optimizer_index(cref::InfOptConstraintRef; 
                     [label::Type{<:AbstractSupportLabel} = PublicLabel,
                     ndarray::Bool = false, kwargs...])
```

`JuMP.optimizer_index`を拡張して、最適化モデルに保存されている再定式化制約に従って`cref`の`MathOptInterface`インデックスを返すようにします。

キーワード引数`label`と`ndarray`は`TranscriptionOpt`が使用するものであり、`kwargs`はユーザー拡張が使用する可能性のある追加の引数を示します。

デフォルトでは、公開サポートに関連する最適化インデックスのみが返され、完全なセットは`label = All`を介してアクセスできます。さらに、無限制約のインデックスはリストとして返されます。ただし、制約が複数の無限パラメータ依存性を持つ場合は、`ndarray = true`を使用することでn次元配列を取得できます。

これらのインデックスに基づく制約を取得するには、[`optimizer_model_constraint`](@ref)を介してクエリすることも役立ちます。同じキーワード引数を使用して一貫性を保つべきです。

拡張の場合、これは[`optimizer_model_constraint`](@ref)が正しく拡張されている場合および/または制約のために[`map_optimizer_index`](@ref)が拡張されている場合にのみ機能します。

**例**

```julia-repl
julia> optimizer_index(c1)
4-element Array{MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}},1}:
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(1)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(2)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(3)
 MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64},MathOptInterface.GreaterThan{Float64}}(4)
```
