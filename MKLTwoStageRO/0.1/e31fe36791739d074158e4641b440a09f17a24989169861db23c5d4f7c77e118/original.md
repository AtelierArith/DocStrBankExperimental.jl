```
TSROModel(fields...)
```

Create an instance of the following two-stage robust optimization model (see `(1)` in `Ref.1` for details): 

```formulation
Min_y c' * y + Max_{u ∈ U} Min_{x ∈ F(y, u)} b' * x

Subject to:

    A * y ≥ d, y ∈ Sy

    F(y, u) = {x ∈ Sx: G * x ≥ h - E * y - M * u}

    U is the uncertainty set
```

where `Sy` and `Sx` are allowed to be nonnegative real-valued spaces or nonnegative mixed integer spaces.

P.S. We hope the following mild assumptions hold (`Ref.1-2`):

  * The Relatively Complete Recourse assumption when `Sx` is a nonnegative real-valued space, i.e., the second-stage decision problem (which is a linear program) is feasible for any given `y` and `u`.
  * When `Sx` is a nonnegative mixed integer space, it has at least one real-valued dimension, i.e., the mixed integer programming recourse problem has at least one continuous recourse variable.
  * The Extended Relatively Complete Recourse property when `Sx` is a nonnegative mixed integer space, i.e., the problem obtained by fixing `y`, `u` and the integer part of `x` (which is a linear program) is always feasible and bounded.
  * When `Sx` is a nonnegative mixed integer space, the feasible set of discrete recouse variables (i.e., the integer part of `x`) is bounded.

# Fields

  * `c::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `c` should be converted into a vector form first, e.g., `c = [2]`.
  * `b::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `b` should be converted into a vector form first, e.g., `b = [1]`.
  * `A::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `A` should be converted into a matrix form first, e.g., `A = [1 2]`, `A = [1; 2;;]` or `A = [0;;]`.
  * `d::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `d` should be converted into a vector form first, e.g., `d = [0]`.
  * `G::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `G` should be converted into a matrix form first, e.g., `G = [1 2]`, `G = [1; 2;;]` or `G = [1;;]`.
  * `h::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `h` should be converted into a vector form first, e.g., `h = [0]`.
  * `E::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `E` should be converted into a matrix form first, e.g., `E = [1 2]`, `E = [1; 2;;]` or `E = [-1;;]`.
  * `M::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `M` should be converted into a matrix form first, e.g., `M = [1 2]`, `M = [1; 2;;]` or `M = [-1;;]`.
  * `Sy::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space. It should be constructed as a vector consisting of (a mixture of) instances of the following three basic data types: `Rplus`, `ZeroOne` and `Zplus`. E.g., `Sy = [ZeroOne()]` denotes an one-dimensional binary space `{0, 1}` and `Sy = [Rplus(2), Zplus(3)]` denotes a five-dimensianal nonnegative mixed integer space `ℝ₊² × ℤ₊³`. Note that the latter is equivalent to `Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`.
  * `Sx::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space. It should be constructed as a vector consisting of (a mixture of) instances of the following three basic data types: `Rplus`, `ZeroOne` and `Zplus`. The construction method is the same as `Sy`.
  * `U::Union{Model, Polyhedron, StandardModel, CombinedModel, Vector{StandardModel}}`: The uncertainty set is allowed to be constructed as a `Model` using package `JuMP.jl`, a `Polyhedron` using package `Polyhedra.jl`, or a `StandardModel`, a `CombinedModel` or a `Vector{StandardModel}` using package [`MKLOneClassSVM.jl`](https://github.com/hanb16/MKLOneClassSVM.jl). This package has integrated some neccessary functions from `JuMP.jl`, `Polyhedra.jl`, `MKLOneClassSVM.jl` and some other related packages, which allows the user to model the uncertainty set conveniently without having to additionally `using/import` the above packages. Please see the `Examples` section for brief usage. P.S.: 1. Only the variables whose name is registered as `u` in a `JuMP` model uncertainty set will be recognized as the uncertainty variables unless there is only one registered variable name (or all variables are anonymous). 2. If the uncertianty set is a MKL-based one, the user should specify an `MKLCCG` algorithm to solve it.

# References

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.
3. Bertsimas, D., & Shtern, S. (2018). A scalable algorithm for two-stage adaptive linear optimization. arXiv preprint arXiv:1807.02812.
4. Han, B. (2024). Multiple kernel learning-aided column-and-constraint generation method.
5. Han, B., Shang, C., & Huang, D. (2021). Multiple kernel learning-aided robust optimization: Learning algorithm, computational tractability, and usage in multi-stage decision-making. European Journal of Operational Research, 292(3), 1004-1018.
