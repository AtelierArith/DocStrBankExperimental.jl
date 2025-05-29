```
test_slope(xs::Array,
           ys::Array;
           slope::Number = 0,
           intercept::Bool = true
)
```

線形回帰を行い、回帰傾きが与えられた傾きと異なるかどうかのp値を返します。与えられるのは以下です。

  * `xs` xの配列、NaNを含む可能性があります
  * `ys` yの配列、NaNを含む可能性があります
  * `slope` テストする傾き
  * `intercept` オプション: trueの場合、フィッティングに切片を使用します
