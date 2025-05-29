```
powm!(B, x; shift = zero(eltype(B)), inverse::Bool = false, kwargs...) -> λ, x, [history]
```

デフォルトでは、`|λ|` が最大の `B` の近似固有対 `(λ, x)` を見つけます。

# 引数

  * `B`: 線形マップ、以下の注記を参照してください。
  * `x`: 正規化された初期推定。必要に応じて複素数演算を使用することを忘れないでください。

## キーワード

  * `tol::Real = eps(real(eltype(B))) * size(B, 2) ^ 3`: 残差ノルムの停止許容誤差;
  * `maxiter::Integer = size(B,2)`: 最大反復回数;
  * `log::Bool`: 各反復での残差ノルムを追跡する;
  * `verbose::Bool`: 反復中の収束情報を印刷する。

!!! note "シフト・インバート"
    `invert = true` および `shift = ...` の場合に $Ax = λx$ にシフト・インバートを適用する際、`B * b` の役割は `inv(A - shift I) * b` を計算することになります。したがって、線形マップ $A$ 自体を渡すのではなく、シフト・インバートの作用を持つ線形マップ `B` を渡してください。固有値は実際の行列 $A$ の固有値に戻されます。


# 戻り値

**`log` が `false` の場合**

  * `λ::Number` レイリー商として計算された近似固有値;
  * `x::Vector` 近似固有ベクトル。

**`log` が `true` の場合**

  * `λ::Number`: レイリー商として計算された近似固有値;
  * `x::Vector`: 近似固有ベクトル;
  * `history`: 収束履歴。

**ConvergenceHistory キー**

  * `:tol` => `::Real`: 停止許容誤差;
  * `:resnom` => `::Vector`: 各反復での残差ノルム。

# 例

```julia
using LinearMaps
σ = 1.0 + 1.3im
A = rand(ComplexF64, 50, 50)
F = lu(A - σ * I)
Fmap = LinearMap{ComplexF64}((y, x) -> ldiv!(y, F, x), 50, ismutating = true)
λ, x = powm(Fmap, inverse = true, shift = σ, tol = 1e-4, maxiter = 200)
```
