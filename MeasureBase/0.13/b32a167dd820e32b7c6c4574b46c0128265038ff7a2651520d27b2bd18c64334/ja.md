```
rootmeasure(μ::AbstractMeasure)
```

測度の固定点を `basemeasure` の下で見つけることが重要な場合があります。つまり、いくつかの測度から始めて、変化がなくなるまで `basemeasure` を繰り返し適用することです。これがこの関数の目的です。
