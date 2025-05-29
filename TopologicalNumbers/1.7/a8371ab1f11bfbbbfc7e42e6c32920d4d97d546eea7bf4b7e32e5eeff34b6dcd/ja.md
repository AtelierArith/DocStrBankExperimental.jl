四次元の場合の第二チェルン数を、福井-初貝-鈴木法 [Fukui2005Chern,Mochol-Grzelak2018Efficient](@cite) に基づいて計算します。

```
solve(prob::SCProblem, alg::T1=FHS2(); parallel::T2=UseSingleThread()) where {T1<:SecondChernAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::SCProblem`: 波数空間におけるハミルトニアン行列関数、充填数、メッシュ数、およびその他のパラメータを含む SCProblem 構造体。
  * `alg::T1=FHS2()`: 第二チェルン数を計算するために使用するアルゴリズム。デフォルトは `FHS2` アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `SCSolution`: 計算された第二チェルン数を含む構造体。

# 例

```julia
julia> H(k) = LatticeDirac(k, -3.0)
julia> prob = SCProblem(H)
julia> result = solve(prob)
SCSolution{Float64}(0.9793607631927381)
julia> result.TopologicalNumber
0.9793607631927381
```
