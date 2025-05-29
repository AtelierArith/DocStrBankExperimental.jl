```
JUA_QualifiedName
```

名前空間インデックスとテキスト部分（名前）で構成される修正可能な構造体で、資格名を定義します。これは `UA_QualifiedName` の同等物ですが、CではなくJuliaによってメモリが管理されます。

以下のコンストラクタメソッドが定義されています：

```
JUA_QualifiedName()
```

空の `JUA_QualifiedName` を作成します。これは `UA_QualifiedName_new()` を呼び出すのと同等です。

```
JUA_QualifiedName(nsIndex::Integer, identifier::AbstractString)
```

名前空間インデックス `nsIndex` とテキスト識別子 `identifier` を持つ `JUA_QualifiedName` を作成します。

```
JUA_QualifiedName(ptr::Ptr{UA_QualifiedName})
```

ポインタ `ptr` に基づいて `JUA_QualifiedName` を作成します。これは、低レベルインターフェースを介して生成された `UA_QualifiedName` を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理がC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合は、`UA_QualifiedName_delete(ptr)` で `ptr` を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。
