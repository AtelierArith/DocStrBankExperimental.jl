```
UA_VariableAttributes_generate(; value::Union{AbstractArray{T}, T},
    displayname::AbstractString, description::AbstractString,
    localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    accesslevel::Union{Nothing, UInt8} = nothing,
    useraccesslevel::Union{Nothing, UInt8} = nothing,
    minimumsamplinginterval::Union{Nothing, Float64} = nothing,
    historizing::Union{Nothing, Bool} = nothing,
    valuerank::Union{Integer, Nothing} = nothing)::Ptr{UA_VariableAttributes} where {T <: Union{UA_NUMBER_TYPES, Complex{Float32}, Complex{Float64}, Rational{Int32}, Rational{UInt32}, AbstractString}}
```

は `UA_VariableAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後に `UA_VariableAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。詳細は `UA_VariableAttributes_default[]` を参照してください。キーワード `valuerank` に何も指定されていない場合、`value` がスカラーであれば `UA_VALUERANK_SCALAR` に設定され、そうでなければ提供された配列の次元数（すなわち、`N` は AbstractArray{T,N} の場合）に設定されます。

それぞれのキーワード入力を生成する方法については、[`UA_WRITEMASK`](@ref)、[`UA_USERWRITEMASK`](@ref)、[`UA_ACCESSLEVEL`](@ref)、および [`UA_USERACCESSLEVEL`](@ref) を参照してください。
