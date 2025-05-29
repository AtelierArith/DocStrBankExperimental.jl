```
struct ValidationViolations <: QuEraSchema
```

ユーザーが提供した [`BloqadeExpr.RydbergHamiltonian`](@ref) からのハードウェア制約の違反を文字列のセットとして保存します。これは [`validate`](@ref) と [`to_schema`](@ref) によって返されます。

# フィールド

  * `lattice_violations::Set`: ハードウェアサポートされた格子幾何学の違反
  * `misc_violations::Set`: 他のカテゴリに該当しない違反（例：ショット数）
  * `Δ_violations::Set`: デチューニング波形の違反
  * `Ω_violations::Set`: ラビ周波数波形の違反
  * `ϕ_violations::Set`: 位相波形の違反
  * `δ_violations::Set`: ローカルデチューニング波形の違反
