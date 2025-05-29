```
UA_ObjectAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    eventnotifier::Union{Nothing, UInt8} = nothing)::Ptr{UA_ObjectAttributes}
```

は `UA_ObjectAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後に `UA_ObjectAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。詳細は `UA_ObjectAttributes_default[]` を参照してください。

また、各キーワード入力を生成する方法については [`UA_WRITEMASK`](@ref)、[`UA_USERWRITEMASK`](@ref)、[`UA_EVENTNOTIFIER`](@ref) を参照してください。
