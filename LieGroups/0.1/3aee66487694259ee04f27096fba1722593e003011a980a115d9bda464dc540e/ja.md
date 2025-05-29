```
lie_bracket(::LieAlgebra{𝔽,AbelianMultiplicationGroupOperation}, X, Y)
lie_bracket!(::LieAlgebra{𝔽,AbelianMultiplicationGroupOperation}, Z, X, Y)
```

リー括弧 $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ を計算します。これは [`AbelianMultiplicationGroupOperation`](@ref) の場合、可換性により [`LieAlgebra`](@ref) のゼロベクトルを生成します。

$$
[X, Y] = XY-YX = 0
$$

計算は `Z` が `mutable` であれば `Z` のインプレースで行うことができます。
