```
JUA_VariableTypeAttributes
```

`JUA_VariableTypeAttributes`オブジェクトを定義する可変構造体 - `UA_VariableTypeAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_VariableTypeAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_VariableTypeAttributes_generate`](@ref)を参照してください。

```
JUA_VariableTypeAttributes(ptr::Ptr{UA_VariableTypeAttributes})
```

ポインタ`ptr`に基づいて`JUA_VariableTypeAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_VariableAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。`UA_VariableAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合、`UA_VariableTypeAttributes_delete(ptr)`で`ptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
