```
kron(A::LinearMap, B::LinearMap)::KroneckerMap
kron(A, B, Cs...)::KroneckerMap
```

`A⊗B`の（遅延）表現を構築します。2つの因子のうちの1つは`AbstractMatrix`であることができ、これは自動的に`LinearMap`に昇格されます。

`kron(A, B, Cs...)`のような使用法では、最初の8つの引数の中に`LinearMap`オブジェクトが存在しなければ、一般的な[`Base.kron`](@ref)にフォールバックすることを避ける必要があります。

便利のために、すべての引数が`AbstractMatrix`型であっても、`A ⊗ B`または`⊗(A, B, Cs...)`（`\otimes+TAB`としてタイプ指定）を使用して`KroneckerMap`を構築することもできます。

`A`、`B`、`C`、および`D`が、行列積`A*C`および`B*D`を形成できるサイズの線形写像である場合、混合積の性質`(A⊗B)*(C⊗D) = (A*C)⊗(B*D)`が成り立ちます。ベクトルの乗算時に、このルールの適用可能性がチェックされます。

# 例

```jldoctest; setup=(using LinearAlgebra, SparseArrays, LinearMaps)
julia> J = LinearMap(I, 2) # 2×2 単位行列写像
2×2 LinearMaps.UniformScalingMap{Bool} with scaling factor: true

julia> E = spdiagm(-1 => trues(1)); D = E + E' - 2I;

julia> Δ = kron(D, J) + kron(J, D); # 離散2Dラプラス演算子

julia> Matrix(Δ)
4×4 Matrix{Int64}:
 -4   1   1   0
  1  -4   0   1
  1   0  -4   1
  0   1   1  -4
```
