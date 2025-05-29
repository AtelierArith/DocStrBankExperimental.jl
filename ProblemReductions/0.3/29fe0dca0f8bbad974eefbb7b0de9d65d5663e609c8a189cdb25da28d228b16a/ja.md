```julia
struct Satisfiability{S, T, WT<:(AbstractArray{T}), OBJ} <: ProblemReductions.AbstractSatisfiabilityProblem{S, T, OBJ}
```

```
Satisfiability(cnf::CNF{S}, weights::AbstractVector=UnitWeight(length(cnf.clauses)); use_constraints::Bool=false) where {S}
```

Satisfiability（SATとも呼ばれる）問題は、論理和標準形（CNF）を満たすブール割り当てを見つけることです。典型的なCNFは次のようになります：

$$
\left(l_{11} \vee \ldots \vee l_{1 n_1}\right) \wedge \ldots \wedge\left(l_{m 1} \vee \ldots \vee l_{m n_m}\right)
$$

ここで、リテラルは$m$個の節を形成するために$\vee$で結合され、節はCNFを形成するために$\wedge$で結合されます。満足度問題は、`use_constraints`が`false`の場合、満たされた節の数を最大化する割り当てを見つけることです。そうでない場合、目標はCNFを満たすことができる1つの割り当てを見つけることです。

すべてのSAT問題は3-SAT問題に還元でき、3-SATがNP完全であることが証明できます。

## フィールド

  * `cnf`は、満足度問題を指定するための論理和標準形（[`CNF`](@ref)）です。
  * `weights`は節に関連付けられています。解のサイズは、満たされた割り当ての数の加重和です。

## 例

以下の例では、2つの節を持つ満足度問題を定義します。

```jldoctest
julia> using ProblemReductions

julia> bv1, bv2, bv3 = BoolVar.(["x", "y", "z"])
3-element Vector{BoolVar{String}}:
 x
 y
 z

julia> clause1 = CNFClause([bv1, bv2, bv3])
x ∨ y ∨ z

julia> clause2 = CNFClause([BoolVar("w"), bv1, BoolVar("x", true)])
w ∨ x ∨ ¬x

julia> cnf_test = CNF([clause1, clause2])
(x ∨ y ∨ z) ∧ (w ∨ x ∨ ¬x)

julia> sat_test = Satisfiability(cnf_test)
Satisfiability{String, Int64, UnitWeight, ProblemReductions.EXTREMA}(["x", "y", "z", "w"], [1, 1], (x ∨ y ∨ z) ∧ (w ∨ x ∨ ¬x))
```
