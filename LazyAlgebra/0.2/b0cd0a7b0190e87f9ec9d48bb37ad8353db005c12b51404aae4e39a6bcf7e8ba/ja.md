```
unscaled(A)
```

は、スケーリングされたマッピング `A = λ*M` のマッピング `M` を返します（[`Scaled`](@ref]を参照）。そうでない場合は `A` を返します。このメソッドは `LinearAlgebra.UniformScaling` のインスタンスにも適用されます。乗数 `λ` を取得するには [`multiplier`](@ref) を呼び出してください。
