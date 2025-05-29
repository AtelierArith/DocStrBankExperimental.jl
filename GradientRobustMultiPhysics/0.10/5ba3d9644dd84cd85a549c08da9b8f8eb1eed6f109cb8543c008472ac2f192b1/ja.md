```
function H1BestapproximationProblem(
    exact_function_gradient::AbstractUserDataType,
    exact_function_boundary::AbstractUserDataType;
    bonus_quadorder::Int = 0,
    bonus_quadorder_boundary::Int = 0,
    bestapprox_boundary_regions = [])
```

与えられた正確な関数（境界でのみ使用）とその正確な勾配（右辺で使用）に対するH1-Bestapproximation問題のためのPDEDescriptionを作成します。このプロトタイプにはすでに境界および右辺データが含まれているため、精度を調整するためにボーナスの数値積分次数を指定することもできます。
