```julia
AB5(; thread = OrdinaryDiffEq.False())
```

アダムス-バッシュフォース明示法 5段階の5次多段法。 ラルストンの3次ルンゲ-クッタ法を使用して初期値を計算します。

### キーワード引数

  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献

E. Hairer, S. P. Norsett, G. Wanner, Solving Ordinary Differential Equations I, Nonstiff Problems. Computational Mathematics (2nd revised ed.), Springer (1996) doi: https://doi.org/10.1007/978-3-540-78862-1
