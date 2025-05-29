```
overapproximate(vTM::Vector{TaylorModel1{T, S}}, ::Type{<:Zonotope};
                [remove_redundant_generators]::Bool=true
                [normalize]::Bool=true) where {T, S}
```

Overapproximate a Taylor model in one variable with a zonotope.

### Input

  * `vTM`       – vector of `TaylorModel1`
  * `Zonotope`  –  target set type
  * `remove_redundant_generators` – (optional; default: `true`) flag to remove                                  redundant generators of the resulting zonotope
  * `normalize` – (optional; default: `true`) flag to skip the normalization of                the Taylor models

### Output

A zonotope that overapproximates the range of the given Taylor model.

### Examples

If the polynomials are linear, this method exactly transforms to a zonotope. The nonlinear case necessarily introduces overapproximation error. Consider the linear case first:

```jldoctest oa_tm1
julia> using LazySets, TaylorModels

julia> const IA = IntervalArithmetic;

julia> I = IA.interval(-0.5, 0.5) # interval remainder
[-0.5, 0.5]

julia> x₀ = IA.interval(0.0) # expansion point
[0, 0]

julia> D = IA.interval(-3.0, 1.0)
[-3, 1]

julia> p1 = Taylor1([2.0, 1.0], 2) # define a linear polynomial
 2.0 + 1.0 t + 𝒪(t³)

julia> p2 = Taylor1([0.9, 3.0], 2) # define another linear polynomial
 0.9 + 3.0 t + 𝒪(t³)

julia> vTM = [TaylorModel1(pi, I, x₀, D) for pi in [p1, p2]]
2-element Vector{TaylorModel1{Float64, Float64}}:
  2.0 + 1.0 t + [-0.5, 0.5]
  0.9 + 3.0 t + [-0.5, 0.5]
```

Here, `vTM` is a Taylor model vector, since each component is a Taylor model in one variable (`TaylorModel1`). Using `overapproximate(vTM, Zonotope)` we can compute its associated zonotope in generator representation:

```jldoctest oa_tm1
julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
2-element Vector{Float64}:
  1.0
 -2.1

julia> Matrix(genmat(Z))
2×3 Matrix{Float64}:
 2.0  0.5  0.0
 6.0  0.0  0.5
```

Note how the generators of this zonotope mainly consist of two pieces: one comes from the linear part of the polynomials, and another one corresponds to the interval remainder. This conversion gives the same upper and lower bounds as the range evaluation using interval arithmetic:

```jldoctest oa_tm1
julia> X = box_approximation(Z)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([1.0, -2.1], [2.5, 6.5])

julia> Y = evaluate(vTM[1], vTM[1].dom) × evaluate(vTM[2], vTM[2].dom)
[-1.5, 3.5] × [-8.60001, 4.40001]

julia> H = convert(Hyperrectangle, Y) # this IntervalBox is the same as X
Hyperrectangle{Float64, StaticArraysCore.SVector{2, Float64}, StaticArraysCore.SVector{2, Float64}}([1.0, -2.1000000000000005], [2.5, 6.500000000000001])
```

However, the zonotope returns better results if we want to approximate the Taylor model because it is not axis-aligned:

```jldoctest oa_tm1
julia> d = [-0.35, 0.93];

julia> ρ(d, Z) < ρ(d, X)
true
```

This method also works if the polynomials are non-linear; for example suppose that we add a third polynomial with a quadratic term:

```jldoctest oa_tm1
julia> p3 = Taylor1([0.9, 3.0, 1.0], 3)
 0.9 + 3.0 t + 1.0 t² + 𝒪(t⁴)

julia> vTM = [TaylorModel1(pi, I, x₀, D) for pi in [p1, p2, p3]]
3-element Vector{TaylorModel1{Float64, Float64}}:
           2.0 + 1.0 t + [-0.5, 0.5]
           0.9 + 3.0 t + [-0.5, 0.5]
  0.9 + 3.0 t + 1.0 t² + [-0.5, 0.5]

julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
3-element Vector{Float64}:
  1.0
 -2.1
  2.4

julia> Matrix(genmat(Z))
3×4 Matrix{Float64}:
 2.0  0.5  0.0  0.0
 6.0  0.0  0.5  0.0
 6.0  0.0  0.0  5.0
```

The last generator corresponds to the addition of the interval remainder and the box overapproximation of the nonlinear part of `p3` over the domain.

### Algorithm

Let $\text{vTM} = (p, I)$ be a vector of $m$ Taylor models, where $I$ is the interval remainder in $ℝ^m$. Let $p_{lin}$ (resp. $p_{nonlin}$) correspond to the linear (resp. nonlinear) part of each scalar polynomial.

The range of $\text{vTM}$ can be enclosed by a zonotope with center $c$ and matrix of generators $G$, $Z = ⟨c, G⟩$, by performing a conservative linearization of $\text{vTM}$:

$$
    vTM' = (p', I') := (p_{lin} − p_{nonlin} , I + \text{Int}(p_{nonlin})).
$$

This algorithm proceeds in two steps:

1- Conservatively linearize $\text{vTM}$ as above and compute a box    overapproximation of the nonlinear part. 2- Transform the linear Taylor model to a zonotope exactly through variable    normalization onto the symmetric intervals $[-1, 1]$.
