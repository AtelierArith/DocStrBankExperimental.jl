```
 partition(c; k, endpoints)
```

`c::Corpus`を長さ`k`（デフォルトは40）の`Vector{Corpus}`に分割します。あるいは、分割のための事前定義された`endpoints`のベクターを提供することもでき、その場合は`k`は無視されます。
