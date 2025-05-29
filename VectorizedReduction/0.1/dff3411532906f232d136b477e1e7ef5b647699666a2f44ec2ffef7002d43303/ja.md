```
vnorm(A::AbstractArray, p::Real=2; dims=:)
```

`A`の次元`dims`に沿った`p`-ノルムを、対応するスライスがベクトルであるかのように計算します。

`p`は任意の数値を取ることができます（すべての値が数学的に有効なベクトルノルムを生成するわけではありません）。`vnorm(A, Inf)`は`abs.(A)`の中で最大の値を返し、`vnorm(A, -Inf)`は最小の値を返します；`vnorm(A, 0)`は`LinearAlgebra.norm(A, 0)`の動作に一致します。

関連情報: [`vtnorm`](@ref)
