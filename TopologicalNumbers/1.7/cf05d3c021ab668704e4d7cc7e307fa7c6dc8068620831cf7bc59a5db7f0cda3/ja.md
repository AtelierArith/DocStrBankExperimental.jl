2次元の場合のベリー流束をFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern](@cite)。

```
solve(prob::LBFProblem, alg::T1=FHSlocal2(); parallel::T2=UseSingleThread()) where {T1<:BerryFluxAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::LBFProblem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含むLBFProblem構造体。
  * `alg::T1=FHSlocal2()`: 第2のチェルン数を計算するために使用するアルゴリズム。デフォルトは`FHSlocal2`アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `LBFSolution`: 計算されたベリー流束を含む構造体。

# 例

```julia
julia> H(k) = Flux2d(k, (6, 1))
julia> n = [0, 0]
julia> prob = LBFProblem(H, n)
julia> result = solve(prob)
LBFSolution{Vector{Int64}, Vector{Int64}}([0, 0, 0, 0, -1, 0], [0, 0])
julia> result.TopologicalNumber
6-element Vector{Int64}:
  0
  0
  0
  0
 -1
  0
```
