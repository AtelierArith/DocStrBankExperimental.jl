```
Z2Solution{T1,T2,T3} <: TopologicalNumbersSolutions
```

`Z2Solution`構造体は、Z2数を計算するための解を表します。

# フィールド

  * `TopologicalNumber::T1`: 各エネルギーバンドのペアに対するZ2数。
  * `TRTopologicalNumber::T2`: ブリルアンゾーンの残りの部分に対するZ2数。このフィールドは、`Z2Problem`で`TR`が`true`のときのみ返されます。
  * `Total::T3`: 総Z2数。
