```
id = ShmId(id)
id = ShmId(shm)
id = ShmId(arr)
id = ShmId(key; readlony=false)
```

最初の引数の値に関連付けられた既存のSystem V共有メモリセグメントの識別子を返します：`id`は共有メモリセグメントの識別子であり、`shm`はSystem V共有メモリオブジェクト、`arr`はSystem V共有メモリセグメントに接続された配列、`key`は共有メモリセグメントに関連付けられたキーです。その場合、キーワード`readlony`を`true`に設定すると読み取り専用アクセスを要求し、それ以外の場合は読み書きアクセスが要求されます。

参照：[`shmid`](@ref)、[`shmget`](@ref)。
