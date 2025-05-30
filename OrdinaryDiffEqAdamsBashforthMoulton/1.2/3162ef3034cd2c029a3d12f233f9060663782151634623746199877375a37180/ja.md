```julia
VCABM3(; thread = OrdinaryDiffEq.False())
```

アダムス明示法 3次アダムス-モールトン法。ボガッキ-シャンピン3/2法が初期値を計算するために使用されます。

### キーワード引数

  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。これは、Juliaが複数のスレッドで起動されたときに適用されます。

## 参考文献

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
