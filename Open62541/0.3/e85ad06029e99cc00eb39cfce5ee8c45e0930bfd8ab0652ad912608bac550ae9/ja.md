```
UA_MethodAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    executable::Union{Nothing, Bool} = nothing,
    userexecutable::Union{Nothing, Bool} = nothing)::Ptr{UA_MethodAttributes}
```

は `UA_MethodAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後は `UA_MethodAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。詳細は `UA_MethodAttributes_default[]` を参照してください。

また、[`UA_WRITEMASK`](@ref) および [`UA_USERWRITEMASK`](@ref) を参照して、該当するキーワード入力を生成する方法についての情報を確認してください。
