```
lastinds(ic::Vector{Int})
```

入力整数ベクトル `ic` の各ユニークな値の最後のインデックス位置を含む整数のベクトルを返します。

`groupinds(unique(A, dim))` から返された出力に対して操作を行うと、返される整数のベクトルは、元の入力多次元配列 `A` の次元 `dim` に沿った各ユニークスライスの最後の位置に対応します。

整数のベクトルのベクトルを受け入れる `firstinds` の実装は、`groupinds(ic::Vector{Int})` から返された出力に対して操作を行います。
