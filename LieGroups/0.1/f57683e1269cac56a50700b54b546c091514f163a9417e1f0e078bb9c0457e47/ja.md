```
lie_bracket(::LieAlgebra{𝔽,MatrixMultiplicationGroupOperation}, X, Y)
lie_bracket!(::LieAlgebra{𝔽,MatrixMultiplicationGroupOperation}, Z, X, Y)
```

リー括弧 $[⋅,⋅]: \mathfrak g×\mathfrak g → \mathfrak g$ を計算します。これは [`MatrixMultiplicationGroupOperation`](@ref) に対して、コムテーター括弧を生成します。

$$
[X, Y] = XY-YX
$$

計算は `Z` のインプレースで行うことができます。
