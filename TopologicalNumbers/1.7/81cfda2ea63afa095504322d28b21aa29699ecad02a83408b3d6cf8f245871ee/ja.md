スライスされた第一チェルン数を三次元の場合において、Fukui-Hatsugai-Suzuki法 [Fukui2005Chern](@cite) を参照して計算します。

```
solve(prob::WCSProblem, alg::T1=FHSsurface(); parallel::T2=UseSingleThread()) where {T1<:WeylPointsAlgorithms,T2<:TopologicalNumbersParallel}
```

# 引数

  * `prob::WCSProblem`: 波数空間におけるハミルトニアン行列関数とその他のパラメータを含むWCSProblem構造体。
  * `alg::T1=FHSsurface()`: スライスされた第一チェルン数を計算するために使用するアルゴリズム。デフォルトは`FHSsurface`アルゴリズムです。
  * `parallel::T2=UseSingleThread()`: 使用する並列化戦略。デフォルトは単一スレッドを使用します。

# 戻り値

  * `WCSSolution`: 計算されたスライスされた第一チェルン数を含む構造体。

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
julia> H(k) = H₀(k, p0);
julia> prob = WCSProblem(H, "k1");
julia> sol = solve(prob)
WCSSolution{String, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}("k1", 6.283185307179587e-5:0.12319971190548208:6.160048427127176, [0 0; 0 0; … ; 0 0; 0 0])
julia> sol.nums
51×2 Matrix{Int64}:
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 1  -1
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
 0   0
```
