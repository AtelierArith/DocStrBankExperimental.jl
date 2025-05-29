```
JUA_ObjectAttributes
```

`JUA_ObjectAttributes`オブジェクトを定義する可変構造体 - `UA_ObjectAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_ObjectAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_ObjectAttributes_generate`](@ref)を参照してください。

```
JUA_ObjectAttributes(ptr::Ptr{UA_ObjectAttributes})
```

ポインタ`ptr`に基づいて`JUA_ObjectAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_ObjectAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。[`UA_ObjectAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理がC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合は、`UA_ObjectAttributes_delete(ptr)`で`ptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
