```
JUA_ObjectTypeAttributes
```

`JUA_ObjectTypeAttributes`オブジェクトを定義する可変構造体 - `UA_ObjectTypeAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_ObjectTypeAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_ObjectTypeAttributes_generate`](@ref)を参照してください。

```
JUA_ObjectTypeAttributes(ptr::Ptr{UA_ObjectTypeAttributes})
```

ポインタ`ptr`に基づいて`JUA_ObjectTypeAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_ObjectTypeAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。[`UA_ObjectTypeAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトがもはや必要でなくなった後、`UA_ObjectTypeAttributes_delete(ptr)`で`ptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
