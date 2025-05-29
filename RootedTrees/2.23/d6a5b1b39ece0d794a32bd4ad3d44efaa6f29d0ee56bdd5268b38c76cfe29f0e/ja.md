```
RosenbrockMethod(γ, A, b, c=vec(sum(A, dims=2)))
```

係数 `γ`、`A`、`b`、および `c` を持つロゼンブロック（またはロゼンブロック-ワナー、ROW）法を表します。`c` が提供されていない場合、自治問題との整合性のために通常の「行和」要件が適用されます。

# 参考文献

  * Ernst Hairer, Gerhard Wanner. Solving ordinary differential equations II: Stiff and differential-algebraic problems. Springer, 2010. Section IV.7
