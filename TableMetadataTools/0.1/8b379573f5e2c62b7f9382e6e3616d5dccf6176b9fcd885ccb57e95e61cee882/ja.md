```
findlabels(predicate, table)
```

`predicate(label(table, column_name))` が `true` を返すすべての値を含む列*名 => 列*ラベルのペアのベクターを返します。これは、`predicate` によって定義されたいくつかの基準を満たすラベルを持つ列名のクイックルックアップを目的としています。

関連情報: [`label`](@ref), [`label!`](@ref), [`labels`](@ref)
