```
JUA_ViewAttributes
```

`JUA_ViewAttributes`オブジェクトを定義する可変構造体 - `UA_ViewAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_ViewAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_ViewAttributes_generate`](@ref)を参照してください。

```
JUA_ViewAttributes(ptr::Ptr{UA_ViewAttributes})
```

ポインタ`ptr`に基づいて`JUA_ViewAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_VariableAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。[`UA_VariableAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理がC側に残ることに注意してください。つまり、オブジェクトがもはや必要でなくなった後に`UA_ViewAttributes_delete(ptr)`で`ptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
