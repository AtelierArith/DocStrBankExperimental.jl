1次元の場合の巻き数をFukui-Hatsugai-Suzuki法に従って計算します [Fukui2005Chern](@cite)。

```
solve(prob::BPProblem, alg::T1=BP(); parallel::T2=UseSingleThread()) where {T1<:BerryPhaseAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::BPProblem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含むBPProblem構造体。
  * `alg::T1=BP()`: ベリー位相を計算するために使用するアルゴリズム。デフォルトは`BP`アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `BPSolution`: 計算されたベリー位相を含む構造体。

# 例

```julia
julia> H(k) = SSH(k, 1.1)
julia> prob = BPProblem(H)
julia> result = solve(prob)
BPSolution{Vector{Int64}, Int64}([1, 1], 0)
julia> result.TopologicalNumber
2-element Vector{Int64}:
 1
 1
```
