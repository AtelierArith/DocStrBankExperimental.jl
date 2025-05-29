Calculate the Weyl points in the three-dimensional case using energy variational method.

```
solve(prob::WPProblem, alg::T1=Evar(); parallel::T2=UseSingleThread()) where {T1<:WeylPointsAlgorithms,T2<:TopologicalNumbersParallel}
```

# Arguments

  * `prob::WPProblem`: The WPProblem struct that contains the Hamiltonian matrix function in the wave number space and other parameters.
  * `alg::T1=Evar()`: The algorithm to use for calculating the Weyl points. Default is `Evar` algorithm.
  * `parallel::T2=UseSingleThread()`: The parallelization strategy to use. Default is to use a single thread.

# Returns

  * `WPSolution`: A struct that contains the calculated Weyl points.

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
julia> prob = WPProblem(H)
julia> result = solve(prob)
WPSolution{Vector{Vector{Vector{Int64}}}, Int64, Vector{Vector{Int64}}}([[[4000, 0, 0], [6000, 0, 0]], [[4000, 0, 0], [6000, 0, 0]]], 10000, [[1, -1], [-1, 1]])
julia> 2pi*result.WeylPoint[1] / result.N .- pi*[ones(3), ones(3)]
2-element Vector{Vector{Float64}}:
 [-0.6283185307179586, -3.141592653589793, -3.141592653589793]
 [0.6283185307179586, -3.141592653589793, -3.141592653589793]
```
