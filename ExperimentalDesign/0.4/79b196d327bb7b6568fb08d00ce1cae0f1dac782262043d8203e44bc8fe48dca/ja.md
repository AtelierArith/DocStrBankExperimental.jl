```julia
OptimalDesign(
    candidates::ExperimentalDesign.AbstractDesign,
    formula::StatsModels.FormulaTerm,
    experiments::Int64;
    tolerance,
    seed_design_size,
    max_iterations,
    design_k,
    candidates_l
) -> ExperimentalDesign.OptimalDesign

```

```jldoctest
julia> design_distribution = DesignDistribution((f1 = Uniform(2, 3), f2 = DiscreteUniform(-1, 5), f3 = Uniform(5, 10)))
DesignDistribution
Formula: 0 ~ f1 + f2 + f3
Factor Distributions:
f1: Uniform{Float64}(a=2.0, b=3.0)
f2: DiscreteUniform(a=-1, b=5)
f3: Uniform{Float64}(a=5.0, b=10.0)

julia> design = rand(design_distribution, 400);

julia> f = @formula 0 ~ f1 + f2 + f3 + f2 ^ 2;

julia> OptimalDesign(design, f, 10)
OptimalDesign
Dimension: (10, 3)
Factors: (f1 = Uniform{Float64}(a=2.0, b=3.0), f2 = DiscreteUniform(a=-1, b=5), f3 = Uniform{Float64}(a=5.0, b=10.0))
Formula: 0 ~ f1 + f2 + f3 + :(f2 ^ 2)
Selected Candidate Rows: [244, 49, 375, 43, 369, 44, 16, 346, 175, 205]
Optimality Criteria: Dict(:D => 2.3940431912232483)
Design Matrix:
10×3 DataFrame
 Row │ f1       f2       f3
     │ Float64  Float64  Float64
─────┼───────────────────────────
   1 │ 2.99329      1.0  5.09246
   2 │ 2.96899      5.0  9.39802
   3 │ 2.96274     -1.0  5.31426
   4 │ 2.00285      2.0  5.40398
   5 │ 2.8491       1.0  9.90621
   6 │ 2.00309     -1.0  9.49394
   7 │ 2.20051      2.0  9.75605
   8 │ 2.06422      5.0  5.1759
   9 │ 2.037       -1.0  9.13114
  10 │ 2.82612      5.0  9.66349

```
