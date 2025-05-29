```
JUA_VariableAttributes
```

`JUA_VariableAttributes`オブジェクトを定義する可変構造体 - `UA_VariableAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については下記参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_VariableAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_VariableAttributes_generate`](@ref)を参照してください。

```
JUA_VariableAttributes(ptr:Ptr{UA_VariableAttributes})
```

ポインタ`ptr`に基づいて`JUA_VariableAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_VariableAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。詳細は[`UA_VariableAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理がC側に残ることに注意してください。つまり、オブジェクトが不要になった後に`UA_VariableAttributes_delete(ptr)`で`ptr`を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
