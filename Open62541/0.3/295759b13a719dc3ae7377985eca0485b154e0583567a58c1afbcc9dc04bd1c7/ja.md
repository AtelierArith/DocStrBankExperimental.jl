```
JUA_LocalizedText
```

ローカライズされたテキストを定義する可変構造体で、ロケール指定子とテキスト部分で構成されています。これは `UA_QualifiedName` の同等物ですが、メモリはCではなくJuliaによって管理されます。

以下のコンストラクタメソッドが定義されています：

```
JUA_LocalizedText()
```

空の `JUA_LocalizedText` を作成します。これは `UA_LocalizedText_new()` を呼び出すのと同等です。

```
JUA_LocalizedText(locale::Union{AbstractString, JUA_String, Ptr{UA_String}}, text::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

ローカライズ `locale` とテキスト `text` を持つ `JUA_LocalizedText` を作成します。

```
JUA_LocalizedText(ptr::Ptr{UA_LocalizedText})
```

ポインタ `ptr` に基づいて `JUA_LocalizedText` を作成します。これは、低レベルインターフェースを介して生成された `UA_LocalizedText` を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトが不要になった後は `UA_LocalizedText_delete(ptr)` で `ptr` を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
