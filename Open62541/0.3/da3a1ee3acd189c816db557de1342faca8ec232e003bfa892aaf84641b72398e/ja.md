```
JUA_NodeId
```

は `JUA_NodeId` オブジェクトを作成します。これは `UA_NodeId` の同等物ですが、C ではなく Julia によってメモリが管理されます。

以下のメソッドが定義されています：

```
JUA_NodeId()
```

は namespaceIndex = 0、numeric identifierType および identifier = 0 の `JUA_NodeId` を作成します。

```
JUA_NodeId(s::AbstractString)
```

は、関連するプロパティに解析される文字列 `s` に基づいて `JUA_NodeId` を作成します。

```
JUA_NodeId(nsIndex::Integer, identifier::Integer)
```

は、namespace index `nsIndex` と数値 identifier `identifier` を持つ `JUA_NodeId` を作成します。

```
JUA_NodeId(nsIndex::Integer, identifier::AbstractString)
```

は、namespace index `nsIndex` と文字列 identifier `identifier` を持つ `JUA_NodeId` を作成します。

```
JUA_NodeId(nsIndex::Integer, identifier::JUA_Guid)
```

は、namespace index `nsIndex` とグローバルユニークID identifier `identifier` を持つ `JUA_NodeId` を作成します。

```
JUA_NodeId(nptr::Ptr{UA_NodeId})
```

は、ポインタ `nptr` に基づいて `JUA_NodeId` を作成します。これは、低レベルインターフェースを介して生成された `UA_NodeId` を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理が C 側に残ることに注意してください。つまり、オブジェクトが不要になった後に `UA_NodeId_delete(nptr)` で `nptr` を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。

例：

```
j = JUA_NodeId()
j = JUA_NodeId("ns=1;i=1234")
j = JUA_NodeId("ns=1;s=example")
j = JUA_NodeId(1, 1234)
j = JUA_NodeId(1, "example")
j = JUA_NodeId(1, JUA_Guid("C496578A-0DFE-4B8F-870A-745238C6AEAE"))
```
