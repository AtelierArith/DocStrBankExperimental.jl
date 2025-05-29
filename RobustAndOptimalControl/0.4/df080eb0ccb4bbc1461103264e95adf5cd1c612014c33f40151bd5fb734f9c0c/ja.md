```
Wh = hanus(W)
```

`Wh`をHanus形式で返します。`Wh`は入力の数が2倍であり、入力の後半は「実際の入力」、つまり潜在的に飽和している可能性があります。これは、`W`にアンチウィンドアップ保護を付与するために使用されます。`W`は可逆な`D`行列を持ち、最小位相でなければなりません。

参照: Skogestadの「Multivariable Feedback Control: Analysis and Design」のセクション9.4.5
