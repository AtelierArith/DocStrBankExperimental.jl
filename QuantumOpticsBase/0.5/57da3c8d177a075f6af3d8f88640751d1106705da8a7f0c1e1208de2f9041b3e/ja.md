```
pauliy([T=ComplexF64,] b::NLevelBasis)
```

与えられた `N` レベルシステムの一般化されたパウリ $Y$ 演算子。

`Y^pow = ω^pow X^pow Z^pow` を返します。ここで `ω = ω = exp(2π*1im*pow/N)` であり、`N` が奇数のときは `N = length(b)`、偶数のときは `N = 2*length(b)` です。これは、偶数次元と奇数次元における一般化されたパウリ群の順序によるものです。

詳細については [`paulix`](@ref) と [`pauliz`](@ref) を参照してください。
