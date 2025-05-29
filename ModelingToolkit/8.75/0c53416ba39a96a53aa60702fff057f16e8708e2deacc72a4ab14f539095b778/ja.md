```julia
add_accumulations(sys, vars)

```

`vars`のための蓄積変数を追加します。`vars`は次の形式のペアのベクトルです。

```julia
[cumulative_var1 => x + y, cumulative_var2 => x^2]
```

その後、累積変数`cumulative_var1`と`cumulative_var2`が追加され、`x + y`と`x^2`の累積を計算します。
