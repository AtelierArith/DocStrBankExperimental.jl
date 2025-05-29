```
function L2BestapproximationProblem(
    uexact::AbstractUserDataType;
    bonus_quadorder::Int = 0,
    bestapprox_boundary_regions = [])
```

与えられた正確な関数のためのL2-Bestapproximation問題のPDEDescriptionを作成します。このプロトタイプにはすでに境界および右辺データが含まれているため、精度を調整するためにボーナスの数値積分次数を指定することもできます。
