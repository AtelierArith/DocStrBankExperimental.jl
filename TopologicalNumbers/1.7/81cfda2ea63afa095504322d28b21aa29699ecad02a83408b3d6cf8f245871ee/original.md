Calculate the sliced first Chern numbers in the three-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
solve(prob::WCSProblem, alg::T1=FHSsurface(); parallel::T2=UseSingleThread()) where {T1<:WeylPointsAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::WCSProblem`: The WCSProblem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=FHSsurface()`: The algorithm to use for calculating the sliced first Chern numbers. Default is `FHSsurface` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `WCSSolution`: A struct that contains the calculated sliced first Chern numbers.

# Examples

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
WCSSolution{String, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}, Matrix{Int64}}("k1", 6.283185307179587e-5:0.12319971190548208:6.160048427127176, [0 0; 0 0; … ; 0 0; 0 0])
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
