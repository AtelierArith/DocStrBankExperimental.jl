```julia
struct MatrixFreeBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}} <: BifurcationKit.AbstractBorderedLinearSolver
```

この構造体は、全システム `(x, p)` に対する行列フリー演算子に基づく境界付き線形ソルバーを提供するために使用されます。

## コンストラクタ

```
MatrixFreeBLS(solver, ::Bool)
```

## フィールド

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: 拡張線形システムを解くための線形ソルバー
  * `use_bordered_array::Bool`: `(x, p)` を保持するために使用される構造。`true` の場合、`BorderedArray` を使用して達成されます。`false` の場合、`Vector` が使用されます。
