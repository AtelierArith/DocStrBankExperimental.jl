$$
\mathbb{Z}_2
$$

数を二次元の場合において Shiozaki メソッド [Fukui2007Quantum,Shiozaki2023discrete](@cite) に基づいて計算します。

```
solve(prob::Z2Problem, alg::T1=Shio(); parallel::T2=UseSingleThread()) where {T1<:Z2Algorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::Z2Problem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含む Z2Problem 構造体。
  * `alg::T1=Shio()`: Z2 数を計算するために使用するアルゴリズム。デフォルトは `Shio` アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `Z2Solution`: 計算された Z2 数を含む構造体。

# 例

```julia
julia> H(k) = KaneMele(k, 1.0)
julia> prob = Z2Problem(H)
julia> result = solve(prob)
Z2Solution{Vector{Int64}, Nothing, Int64}([1, 1], nothing, 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
 1
 1
```
