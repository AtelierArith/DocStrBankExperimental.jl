```
JUA_CallMethodRequest
```

`JUA_CallMethodRequest`オブジェクトを定義する可変構造体 - `UA_CallMethodRequest`の同等物ですが、CではなくJuliaによってメモリが管理されます（以下の例外を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_CallMethodRequest()
```

空の`JUA_CallMethodRequest`を作成します。これは`UA_CallMethodRequest_new()`を呼び出すのと同等です。

```
JUA_CallMethodRequest(objectid::JUA_NodeId, methodid::JUA_NodeId, inputarg::Union{Any, Tuple{Any, ...}})
```

コンテキストノードID（`objectid`）、呼び出すメソッドのノードID（`methodid`）、およびメソッドが呼び出される`inputarg`を取る`JUA_CallMethodRequest`を作成します。

`inputarg`はOpen62541.jl内で互換性のある任意の型であり、特に組み込みの数値型、文字列、UA_XXX型などが含まれます。入力引数は配列（例えば、Vector{Float64}）でも構いません。複数の引数はタプルとして提供する必要があります。

```
JUA_CallMethodRequest(methodrequestptr::Ptr{UA_CallMethodRequest})
```

ポインタ`methodrequestptr`に基づいて`JUA_CallMethodRequest`を作成します。これは、低レベルインターフェースを介して生成された`UA_CallMethodRequest`を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトが不要になった後に`UA_CallMethodRequest_delete(methodrequestptr)`で`methodrequestptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。

例：

```
j = JUA_CallMethodRequest()
j = JUA_CallMethodRequest(JUA_NodeId(0, UA_NS0ID_OBJECTSFOLDER), JUA_NodeId(1, 1234), ["Peter", "Julia"]) #文字列のベクターinputarg
j = JUA_CallMethodRequest(JUA_NodeId(0, UA_NS0ID_OBJECTSFOLDER), JUA_NodeId(1, 1234), ("Claudia", 1234)]) #二つの入力引数
```

参照：

  * [`UA_MethodCallback_generate`](@ref)
  * [`UA_MethodCallback_wrap`](@ref)
  * [`JUA_Server_addNode`](@ref)
