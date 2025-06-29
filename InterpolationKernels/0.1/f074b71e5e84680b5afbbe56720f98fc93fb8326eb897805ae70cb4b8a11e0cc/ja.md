```
QuadraticSpline([T=Float64,] B=Flat)
```

は、浮動小数点型 `T` と境界条件 `B` のための二次スプラインのインスタンスを生成します。

二次スプラインは、次のように定義される3次（2次）Bスプラインです：

```
ker(x) = 3/4 - x^2                   もし |x| ≤ 1/2 の場合
         (1/2)*(|x| - 3/2)^2         もし |x| ≤ 3/2 の場合
         0                           もし |x| ≥ 3/2 の場合
```

式 `ker'` は、二次スプライン `ker` の1次導関数であるカーネルインスタンスを生成します（コンストラクタ [`QuadraticSplinePrime`](@ref) も参照してください）。
