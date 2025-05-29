```
JUA_NodeId
```

は `JUA_ExpandedNodeId` オブジェクトを作成します。これは `UA_ExpandedNodeId` の同等物ですが、メモリはCではなくJuliaによって管理されます。

関連情報: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part6/v105/docs/5.2.2.10)

以下のメソッドが定義されています：

```
JUA_ExpandedNodeId()
```

すべてのフィールドがnullに等しい `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(s::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

文字列 `s` に基づいて `JUA_ExpandedNodeId` を作成し、関連するプロパティに解析されます。

```
JUA_ExpandedNodeId(nsIndex::Integer, identifier::Integer)
```

名前空間インデックス `nsIndex`、数値ノードID識別子 `identifier`、serverIndex = 0、および空のnameSpaceUriを持つ `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(nsIndex::Integer, identifier::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

名前空間インデックス `nsIndex`、文字列ノードID識別子 `identifier`、serverIndex = 0、および空のnameSpaceUriを持つ `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(nodeId::Union{Ptr{UA_NodeId}, JUA_NodeId})
```

空のnamespaceUri、serverIndex = 0、および `nodeId` の内容をノードIDフィールドに持つ `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(identifier::Integer, ns_uri::AbstractString, server_ind::Integer) 
```

名前空間インデックス `nsIndex` とグローバルユニークID識別子 `identifier` を持つ `JUA_ExpandedNodeId` を作成し、Nodeidのために、serverIndex = 0 および空のnamespaceUriを持ちます。

```
JUA_ExpandedNodeId(identifier::Union{Ptr{UA_String}, AbstractString, JUA_String}, ns_uri::AbstractString, server_ind::Integer) 
```

ノードIDのための文字列 `identifier`、namespaceUri `ns_uri` およびサーバーインデックス `server_ind` を持つ `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(guid::Union{Ptr{UA_Guid}, JUA_Guid}, ns_uri::AbstractString, server_ind::Integer) 
```

ノードIDがグローバルユニーク識別子 `guid`、namespaceUri `ns_uri` およびサーバーインデックス `server_ind` を持つ `JUA_ExpandedNodeId` を作成します。

```
JUA_ExpandedNodeId(nodeid::Union{Ptr{UA_NodeId}, JUA_NodeId}, ns_uri::AbstractString, server_ind::Integer)
```

JUA*NodeId `nodeid` から `JUA_ExpandedNodeId` を作成し、namespaceUri `ns*uri`およびサーバーインデックス`server_ind` を持ちます。

```
JUA_ExpandedNodeId(nptr::Ptr{UA_ExpandedNodeId})
```

ポインタ `nptr` に基づいて `JUA_ExpandedNodeId` を作成します。これは、低レベルインターフェースを介して生成された `UA_NodeId` を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトが不要になった後、`UA_ExpandedNodeId_delete(nptr)` で `nptr` を手動でクリーンアップする必要があります。これを保証するのはユーザーの責任です。

例：

```
j = JUA_ExpandedNodeId()
j = JUA_ExpandedNodeId("ns=1;i=1234")
j = JUA_ExpandedNodeId("ns=1;s=example")
j = JUA_ExpandedNodeId(1, 1234)
j = JUA_ExpandedNodeId(1, "example")
j = JUA_ExpandedNodeId(1, JUA_Guid("C496578A-0DFE-4B8F-870A-745238C6AEAE"))
```
