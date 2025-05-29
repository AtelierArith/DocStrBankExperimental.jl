```
UA_ViewAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    containsnoloops::Union{Nothing, Bool} = nothing,
    eventnotifier::Union{Nothing, UInt8} = nothing)::Ptr{UA_ViewAttributes}
```

は `UA_ViewAttributes` オブジェクトを生成します。オブジェクトのメモリは C によって割り当てられ、使用後に `UA_ViewAttributes_delete(x)` を呼び出してクリーンアップする必要があります。

`nothing` として指定されたキーワードには、それぞれのデフォルト値が使用されます。詳細は `UA_ViewAttributes_default[]` を参照してください。

また、[`UA_WRITEMASK`](@ref)、[`UA_USERWRITEMASK`](@ref)、および [`UA_EVENTNOTIFIER`](@ref) を参照して、各キーワード入力を生成する方法についての情報を確認してください。
