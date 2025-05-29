三次元の場合のWeylノードをFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern](@cite)。

```
solve(prob::WNProblem, alg::T1=FHSlocal3(); parallel::T2=UseSingleThread()) where {T1<:WeylPointsAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::WNProblem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含むWNProblem構造体。
  * `alg::T1=FHSlocal3()`: Weylノードを計算するために使用するアルゴリズム。デフォルトは`FHSlocal3`アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `WNSolution`: 計算されたWeylノードを含む構造体。

# 例

```julia
julia> function H₀(k, p) # Weyl
    k1, k2, k3 = k
    t1, t2, t3, m, k0 = p

    h0 = 0
    hx = 2t1*(cos(k1) - cos(k0)) + m*(2 - cos(k2) - cos(k3))
    hy = 2t2*sin(k2)
    hz = 2t3*sin(k3)

    s0 = [1 0; 0 1]
    sx = [0 1; 1 0]
    sy = [0 -im; im 0]
    sz = [1 0; 0 -1]

    h0 .* s0 .+ hx .* sx .+ hy .* sy .+ hz .* sz
end
julia> p0 = (1, 1, 1, 2, 2pi*2/5);
julia> H(k) = H₀(k .- 2pi*1e-5, p0);
julia> weylPoint = [4000, 0, 0];
julia> N = 10000;
julia> prob = WNProblem(H, weylPoint, N);
julia> sol = solve(prob)
WNSolution{Vector{Int64}, Vector{Int64}, Int64}([1, -1], [4000, 0, 0], 10000)
julia> sol.TopologicalNumber
2-element Vector{Int64}:
  1
 -1
```
