```
JarqueBeraTestPooled(ud::UncertainDataset, n::Int = 1000) -> JarqueBeraTest
```

まず、`ud`内の各不確実な値の`n`回の実現を描き、それらを一緒にプールします。次に、プールの値が正規分布しているという帰無仮説を検定するために、ジャルク・ベラ統計量を計算します。
