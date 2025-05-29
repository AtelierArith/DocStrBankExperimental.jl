```
fill_surrogate_test!(test::SurrgateTest) → rval, vals
```

`test`によって予想される計算を実行し、実データの識別統計量の値`rval`とサロゲートの値の分布`vals`を返します。

この関数は`pvalue`によって呼び出されます。
