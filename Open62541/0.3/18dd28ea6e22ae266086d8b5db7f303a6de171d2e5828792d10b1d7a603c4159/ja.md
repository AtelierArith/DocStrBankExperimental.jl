```
UA_NodeTypeLifeCycleCallback_destructor_generate(f::Function)
```

は、`UA_NodeTypeLifeCycle` オブジェクトの `destructor` フィールドのための関数ポインタを作成します。

`f` は、以下のシグネチャを持つ Julia 関数でなければなりません：

```
f(server::Ptr{UA_Server}, sessionId:: Ptr{UA_NodeId},
       sessionContext::Ptr{Cvoid}, typeNodeId::Ptr{UA_NodeId}, typeNodeContext::Ptr{Cvoid}, 
       nodeId::Ptr{UA_NodeId}, nodeContext::Ptr{Ptr{Cvoid}})::Cvoid
```
