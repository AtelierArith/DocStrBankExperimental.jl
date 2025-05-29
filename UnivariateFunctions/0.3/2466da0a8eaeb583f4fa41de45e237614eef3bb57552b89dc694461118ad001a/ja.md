```
trim_piecewise_function(func::Piecewise_Function, left_limit::Real, right_limit::Real)
```

これは、区分関数の端をトリミングします。したがって、-10から10の間にサポートがある区分関数がある場合、それを-5から5の間だけサポートを持つようにトリミングできます。次に、-5から5の外で評価されると未定義になります。

### 入力

  * `func` - 区分関数。
  * `left_limit` - 左の制限。
  * `right_limit` - 右の制限。

### 戻り値

  * 区分関数。
