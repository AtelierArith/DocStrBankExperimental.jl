```
grid!(content::Vararg{Pair}; kwargs...)
```

`content`に含まれるすべてのペアを持つGridLayoutを作成します。各ペアは、行と列のスパンを持つイテラブルとコンテンツオブジェクトで構成されています。各コンテンツオブジェクトは、そのペアからのスパンでGridLayoutに配置されます。

例:

grid!(     [1, 1] => obj1,     [1, 2] => obj2,     [2, :] => obj3, )
