```
value(z::BoolExpr)
value(z::Array{BoolExpr})
```

`z`の満たす割り当てを返します。満たす割り当てが知られていない場合は`nothing`を返します。配列の場合は、`Array{Bool}`または`Array{nothing}`を返します。

`Bool`と`nothing`の混合配列を返すことも可能です。これは、配列内のいくつかの変数が問題に現れない場合に発生する可能性があります。なぜなら、`sat!(problem)`は`problem`に現れない変数の値を設定しないからです。
