```julia
struct DefaultLS <: BifurcationKit.AbstractDirectLinearSolver
```

この構造体はバックスラッシュ演算子を提供するために使用されます ``.` (a₀ * I + a₁ * J) * x = rhs` を解くために使用できます。

## フィールド

  * `useFactorization::Bool`: 複数の解法のために因数分解をキャッチするかどうか。いくつかの演算子はLU（ApproxFun.jlのように）やQR因数分解をサポートしていない場合があるため、ユーザーに決定させるのが最良です。いくつかの行列は `factorize` を持っていない（StaticArrays.MMatrixのように）。デフォルト: true
