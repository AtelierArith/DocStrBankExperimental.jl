```
UA_MethodCallback_generate(f::Function)
```

は、`UA_Server_addMethodNode`を使用してメソッドノードに添付できる`UA_MethodCallback`を作成します。

`f`は、次のシグネチャを持つJulia関数でなければなりません：

```
f(server::Ptr{UA_Server}, sessionId::Ptr{UA_NodeId}), sessionContext::Ptr{Cvoid}`, 
    methodId::Ptr{UA_NodeId}, methodContext::Ptr{Cvoid}, objectId::Ptr{UA_NodeId},   
    objectContext::Ptr{Cvoid}, inputSize::Csize_t, input::Ptr{UA_Variant},   
    outputSize::Csize_t, output::Ptr{UA_Variant})::UA_StatusCode
```

もし`f`の出力が入力のみに依存し、セッション状態変数には依存しない場合は、[`UA_MethodCallback_wrap`](@ref)の使用を検討してください。
