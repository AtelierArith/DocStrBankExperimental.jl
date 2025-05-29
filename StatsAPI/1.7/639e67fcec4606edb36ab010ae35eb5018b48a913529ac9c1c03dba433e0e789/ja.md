```
adjr2(model::StatisticalModel)
adjr²(model::StatisticalModel)
```

調整済み決定係数（調整済みR二乗）。

線形モデルの場合、調整済みR²は$1 - (1 - (1-R^2)(n-1)/(n-p))$として定義され、ここで$R^2$は決定係数、$n$は観測数、$p$は係数の数（切片を含む）です。この定義は一般的にWherryの公式Iとして知られています。
