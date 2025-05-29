```
AllocBuffer{StorageType}
```

これは、`StorageType`型の固定量のメモリを格納するために使用できるシンプルなバンプアロケータです。`::StorageType`が`pointer`および`sizeof`をサポートしている限り、使用できます。

使用中のAllocBufferのフィールドを手動で操作しないでください。
