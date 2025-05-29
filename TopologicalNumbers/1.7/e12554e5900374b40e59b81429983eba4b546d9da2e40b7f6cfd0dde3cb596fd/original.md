Calculate the Weyl node in the three-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite).

```
solve(prob::WNProblem, alg::T1=FHSlocal3(); parallel::T2=UseSingleThread()) where {T1<:WeylPointsAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::WNProblem`: The WNProblem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=FHSlocal3()`: The algorithm to use for calculating the Weyl nodes. Default is `FHSlocal3` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `WNSolution`: A struct that contains the calculated Weyl nodes.

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
