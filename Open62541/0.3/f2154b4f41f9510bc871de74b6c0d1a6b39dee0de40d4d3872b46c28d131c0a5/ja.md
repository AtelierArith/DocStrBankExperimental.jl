```
UA_VariableTypeAttributes_generate(; value::Union{Nothing, AbstractArray{T}, T} = nothing,
    displayname::AbstractString, description::AbstractString,
    localization::AbstractString = "ja",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    valuerank::Union{Nothing, Integer} = nothing,
    isabstract::Union{Nothing, Bool})::Ptr{UA_VariableTypeAttributes} where {T <: Union{Nothing, UA_NUMBER_TYPES, Complex{Float32}, Complex{Float64}, Rational{Int32}, Rational{UInt32}, AbstractString}}
```

`UA_VariableTypeAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後に `UA_VariableTypeAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。デフォルトの `value` が変数タイプに指定され、キーワード `valuerank` に何も指定されていない場合、`value` がスカラーであれば `UA_VALUERANK_SCALAR` に設定され、供給された配列の次元数（すなわち、`N` は AbstractArray{T,N} の場合）に設定されます。

それぞれのキーワード入力を生成する方法については、[`UA_WRITEMASK`](@ref)、[`UA_USERWRITEMASK`](@ref) を参照してください。
