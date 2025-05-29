```
BlockDescription
```

[`LinearMixedModel`](@ref)における`A`と`L`のブロックの説明

## フィールド

  * `blknms`: ブロック名のVector{String}
  * `blkrows`: 各ブロックの行数のVector{Int}
  * `ALtypes`: `A`と`L`のブロックのデータ型のMatrix{String}。

`L`のブロックが`A`の対応するブロックと同じ型である場合、`Dense`のように単一の名前で説明されます。型が異なる場合、`ALtypes`のエントリは`shorttype`メソッドによって決定される`Diag/Dense`の形式になります。
