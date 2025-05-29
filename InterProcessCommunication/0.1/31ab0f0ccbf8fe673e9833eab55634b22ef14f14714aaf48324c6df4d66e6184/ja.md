```
shmrm(arg)
```

は、`arg`に関連付けられた共有メモリを削除します。`arg`が名前の場合、対応するPOSIX名付き共有メモリがリンク解除されます。`arg`がBSD共有メモリセグメントのキーまたは識別子の場合、そのセグメントは最終的に破棄されるようにマークされます。引数`arg`は`SharedMemory`オブジェクトでも構いません。

`rm`メソッドも、既存の共有メモリセグメントまたはオブジェクトを削除するために呼び出すことができます。いくつかの可能性があります：

```julia
rm(SharedMemory, name)  # `name`はPOSIX共有メモリオブジェクトを識別します
rm(SharedMemory, key)   # `key`はBSD共有メモリセグメントに関連付けられています
rm(id)                  # `id`はBSD共有メモリセグメントの識別子です
rm(shm)                 # `shm`は`SharedMemory`のインスタンスです
```

参照：[`SharedMemory`](@ref)、[`shmid`](@ref)、[`shmat`](@ref)。
