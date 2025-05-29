```
JUA_MethodAttributes
```

`JUA_MethodAttributes`オブジェクトを定義する可変構造体 - `UA_MethodAttributes`の同等物ですが、CではなくJuliaによってメモリが管理されます（例外については以下を参照）。

以下のコンストラクタメソッドが定義されています：

```
JUA_MethodAttributes(; kwargs...)
```

有効なキーワード引数`kwargs`については[`UA_MethodAttributes_generate`](@ref)を参照してください。

```
JUA_MethodAttributes(ptr::Ptr{UA_MethodAttributes})
```

ポインタ`ptr`に基づいて`JUA_MethodAttributes`を作成します。これは、低レベルインターフェースを介して生成された`UA_MethodAttributes`を高レベル関数に渡すために使用できるフォールバックメソッドです。[`UA_MethodAttributes_generate`](@ref)も参照してください。

このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合、`ptr`は手動で`UA_MethodAttributes_delete(ptr)`でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
