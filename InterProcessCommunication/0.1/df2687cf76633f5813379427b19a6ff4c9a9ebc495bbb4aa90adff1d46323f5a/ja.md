```
shmctl(id, cmd, buf)
```

は、`id` で指定された System V 共有メモリセグメントに対して `cmd` で指定された制御操作を実行します。`buf` 引数は、`shmid_ds` C 構造体を格納するのに十分な大きさのバイト配列です。

他にも [`shminfo`](@ref)、[`shmcfg`](@ref) および [`shmrm`](@ref) を参照してください。
