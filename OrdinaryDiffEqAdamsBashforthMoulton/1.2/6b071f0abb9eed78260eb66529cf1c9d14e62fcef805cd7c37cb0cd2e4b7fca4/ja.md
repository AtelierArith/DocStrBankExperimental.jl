```julia
VCABM(; thread = OrdinaryDiffEq.False())
```

適応次数アダムス明示法は、適応次数の適応時間アダムスモールトン法です。これは、ShampineのDDEABMから導出された次数適応アルゴリズムを使用します。

### キーワード引数

  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用すべきか（`thread = OrdinaryDiffEq.True()`）を決定します。これは、Juliaが複数のスレッドで起動されたときに適用されます。

## 参考文献

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
