```
consolidate_levels(iter, levels)
```

与えられたレベルに対して `consolidate` を適用します。イテレータからインデックス可能なものに変換します。`consolidate` は基本的に `collect` ですが、`Vectors` を返すのではなく、インデックス可能な何かを返します。

すべてのレベルに対してこれを行うためのエイリアスである `full_consolidate` も参照してください。
