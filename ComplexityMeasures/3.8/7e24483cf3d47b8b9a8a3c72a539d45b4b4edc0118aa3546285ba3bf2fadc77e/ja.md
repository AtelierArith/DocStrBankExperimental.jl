```
Counts <: Array{<:Integer, N}
Counts(counts [, outcomes [, dimlabels]]) → c
```

`Counts`は、`outcomes`のセットに対応する整数`counts`の`N`次元配列を格納します。これは通常「頻度表」または["コンティンジェンシー テーブル"](https://en.wikipedia.org/wiki/Contingency_table)と呼ばれます。

もし`c isa Counts`であれば、`c.outcomes[i]`は`i`-次元に沿った結果を含む抽象ベクターであり、`c[i][j]`は結果`c.outcomes[i][j]`に対応するカウントであり、`c.dimlabels[i]`は`i`-次元のラベルです。ラベルと結果は、指定されていない場合は自動的に割り当てられます。`c`自体は、その格納された配列のように操作および反復処理できます。
