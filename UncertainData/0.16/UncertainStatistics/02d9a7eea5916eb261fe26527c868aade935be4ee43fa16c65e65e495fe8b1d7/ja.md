```
OneSampleADTestElementWise(ud::UncertainDataset,
    n::Int = 1000) -> Vector{JarqueBeraTest}
```

まず、`ud`内の各不確実な値の`n`回の実現を描き、それぞれの不確実な値に対して値のプールを1つ保持します。

次に、各値のプールが正規分布しているという帰無仮説を検定するために、ジャルク・ベラ統計量を計算します。
