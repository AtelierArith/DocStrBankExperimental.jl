```
JUA_DataTypeAttributes
```

`JUA_DataTypeAttributes`オブジェクトを定義する可変構造体 - `UA_DataTypeAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_DataTypeAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_DataTypeAttributes_generate`](@ref)を参照してください。

```
JUA_DataTypeAttributes(ptr::Ptr{UA_DataTypeAttributes})
```

ポインタ`ptr`に基づいて`JUA_DataTypeAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_VariableAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。`UA_VariableAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合、`ptr`は手動で`UA_DataTypeAttributes_delete(ptr)`でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
