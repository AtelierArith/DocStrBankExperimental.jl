```
UA_ReferenceTypeAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    isabstract::Union{Nothing, Bool} = nothing
    symmetric::Union{Nothing, Bool} = nothing,
    inversename::Union{Nothing, AbstractString} = nothing)::Ptr{UA_ReferenceTypeAttributes}
```

は `UA_ReferenceTypeAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後は `UA_ReferenceTypeAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。詳細は `UA_ReferenceTypeAttributes_default[]` を参照してください。

また、[`UA_WRITEMASK`](@ref) および [`UA_USERWRITEMASK`](@ref) を参照して、該当するキーワード入力を生成する方法についての情報を確認してください。
