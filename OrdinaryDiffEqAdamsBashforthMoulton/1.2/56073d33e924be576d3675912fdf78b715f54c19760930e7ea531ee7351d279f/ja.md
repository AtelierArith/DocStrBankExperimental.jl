```julia
AB4(; thread = OrdinaryDiffEq.False())
```

アダムス-バッシュフォース明示法 4段階の4次多段法。 4次のルンゲ-クッタ法が初期値を計算するために使用されます。

### キーワード引数

  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するかを決定します（`thread = OrdinaryDiffEq.True()`）。

## 参考文献

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
