```
id = shmcfg(arg, perms) -> id
```

は、`arg`によって識別されるSystem V IPC共有メモリセグメントのアクセス権限を変更します。`arg`は、System V IPC共有メモリ識別子、System V IPC共有メモリセグメントに接続された共有配列、または共有メモリセグメントに関連付けられたSystem V IPCキーのいずれかです。引数`perms`は、新しい権限を持つビットフラグを指定します。共有メモリセグメントの識別子が返されます。

関連情報としては、[`ShmId`](@ref)、[`shmget`](@ref)、[`shmctl`](@ref)、および[`SharedMemory`](@ref)を参照してください。
