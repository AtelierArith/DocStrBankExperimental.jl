```julia
add_accumulations(sys, vars)

```

`vars`の累積変数を追加します。`vars`は次の形式のペアのベクトルです。

```julia
[cumulative_var1 => x + y, cumulative_var2 => x^2]
```

その後、累積変数`cumulative_var1`と`cumulative_var2`が追加され、累積`x + y`と`x^2`が計算されます。
