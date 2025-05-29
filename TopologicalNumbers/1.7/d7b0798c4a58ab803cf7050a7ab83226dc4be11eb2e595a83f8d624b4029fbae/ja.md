2次元の場合の最初のチェルン数を福井-初貝-鈴木法に基づいて計算します [Fukui2005Chern](@cite)。

```
solve(prob::FCProblem, alg::T1=FHS(); parallel::T2=UseSingleThread()) where {T1<:FirstChernAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::FCProblem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含むFCProblem構造体。
  * `alg::T1=FHS()`: 最初のチェルン数を計算するために使用するアルゴリズム。デフォルトは`FHS`アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `FCSolution`: 計算された最初のチェルン数を含む構造体。

# 例

```julia
julia> H(k) = Haldane(k, (1, 0.5, 1.0))
julia> prob = FCProblem(H)
julia> result = solve(prob)
FCSolution{Vector{Int64}, Int64}([1, -1], 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
  1
 -1
```
