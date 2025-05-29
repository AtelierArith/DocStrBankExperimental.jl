```
(p::Plan)'
adjoint(p::Plan)
```

元のプランの随伴操作を実行するプランを返します。

!!! warning
    随伴プランは現在 `LinearAlgebra.mul!` をサポートしていません。さらに、`AbstractFFTs` への新しい追加として、下流の実装における `Base.adjoint` のカバレッジは限られている可能性があります。

