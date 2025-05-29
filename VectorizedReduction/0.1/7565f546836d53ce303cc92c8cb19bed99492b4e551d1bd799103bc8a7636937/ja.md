```
vtnorm(A::AbstractArray, p::Real=2; dims=:)
```

`A`の次元`dims`に沿った`p`-ノルムを、対応するスライスがベクトルであるかのように計算します。スレッド対応。

`p`は任意の数値を取ることができます（すべての値が数学的に有効なベクトルノルムを生成するわけではありません）。`vtnorm(A, Inf)`は`abs.(A)`の中で最も大きな値を返し、`vtnorm(A, -Inf)`は最も小さな値を返します；`vnorm(A, 0)`は`LinearAlgebra.norm(A, 0)`の動作に一致します。

参照：[`vnorm`](@ref)
