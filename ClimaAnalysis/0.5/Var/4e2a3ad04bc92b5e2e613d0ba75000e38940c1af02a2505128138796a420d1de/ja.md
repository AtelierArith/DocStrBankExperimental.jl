```
make_lonlat_mask(var;
                 set_to_val = nothing,
                 true_val = NaN,
                 false_val = 1.0)
```

`OutputVar`を受け取り、`var.data`を使用してデータをマスクするマスキング関数を返します。

パラメータ`set_to_val`は、`var.data`の要素を受け取り、`true`または`false`を返す関数です。`set_to_nan`が`true`を返すと、マスク内の値は`true_val`になり、`set_to_nan`が`false`を返すと、マスク内の値は`false_val`になります。

`set_to_nan`が`nothing`の場合、変換は行われず、`var.data`が使用されます。これは、`var.data`がすでにNaNと1の配列または0と1の配列である場合に便利です。
