```julia
VCAB3(; thread = OrdinaryDiffEq.False())
```

アダムス明示法 3次のアダムス法。ボガッキ-シャンピン 3/2 法が初期値を計算するために使用されます。

### キーワード引数

  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するかを決定します（`thread = OrdinaryDiffEq.True()`）。

## 参考文献

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
