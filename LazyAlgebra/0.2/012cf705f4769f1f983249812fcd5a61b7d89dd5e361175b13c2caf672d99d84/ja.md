```
multiplier(A)
```

はスケーリングされたマッピング `A = λ*M` の乗数 `λ` を返します（[`Scaled`](@ref]を参照）。そうでない場合は `1` を返します。このメソッドは `LinearAlgebra.UniformScaling` のインスタンスにも適用されます。マッピング `M` を取得するには [`unscaled`](@ref) を呼び出してください。 `λ`。
