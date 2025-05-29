```
MultTable(ops::AbstractVector, modτ=true)
```

`ops`の可算な`SymOperation`の乗法（またはケイリー）テーブルを計算します。

`row`および`col`演算子の合成から得られる対称操作を含む`MultTable`が返されます。インデックスのテーブルは、`ops`の順序に対する対称演算子を示します。

## キーワード引数

  * `modτ`（デフォルト: `true`）：演算の合成が格子ベクトルに対して剰余を取るか（`true`）どうか（`false`）を指定します。
