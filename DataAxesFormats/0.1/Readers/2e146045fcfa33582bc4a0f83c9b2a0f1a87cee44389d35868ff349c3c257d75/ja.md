```
description(daf::DafReader[; deep::Bool = false, cache::Bool = false])::AbstractString
```

`daf`の内容についての（複数行の）説明を返します。これは有用性と簡潔さの間の良いバランスを取ることを試みます。`cache`が真の場合、キャッシュの内容についても説明します。`deep`が真の場合、このデータセットの内部にネストされているデータセットについても説明します（もしあれば）。
