```
line_regress(
            xs::Array,
            ys::Array;
            intercept::Bool = true,
            sorting::Bool = true
)
```

線形回帰を行い、適合した結果を返します。与えられたものは次のとおりです。

  * `xs` xの配列、NaNを含む可能性があります
  * `ys` yの配列、NaNを含む可能性があります
  * `intercept` オプション: trueの場合、フィッティングに切片を使用します
  * `sorting` オプション: trueの場合、値をソートします
