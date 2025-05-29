```julia
rand(
    distribution::ExperimentalDesign.DesignDistribution
) -> ExperimentalDesign.RandomDesign
rand(
    distribution::ExperimentalDesign.DesignDistribution,
    n::Int64
) -> ExperimentalDesign.RandomDesign

```

```jldoctest
julia> rand(DesignDistribution((f1 = Uniform(2, 3), f2 = DiscreteUniform(-1, 5), f3 = Uniform(5, 10))), 12)
ExperimentalDesign.RandomDesign
Dimension: (12, 3)
Factors: (f1 = Uniform{Float64}(a=2.0, b=3.0), f2 = DiscreteUniform(a=-1, b=5), f3 = Uniform{Float64}(a=5.0, b=10.0))
Formula: 0 ~ f1 + f2 + f3
Design Matrix:
12×3 DataFrame
 Row │ f1       f2       f3
     │ Float64  Float64  Float64
─────┼───────────────────────────
   1 │ 2.04922     -1.0  9.62061
   2 │ 2.59117      3.0  5.79254
   3 │ 2.77148     -1.0  6.22902
   4 │ 2.25659      4.0  6.00256
   5 │ 2.64968      2.0  9.21818
   6 │ 2.31523      5.0  8.80749
   7 │ 2.86526      2.0  8.47297
   8 │ 2.44753      0.0  6.11722
   9 │ 2.08284     -1.0  6.34626
  10 │ 2.81201     -1.0  6.44508
  11 │ 2.64232      3.0  5.57183
  12 │ 2.08189      1.0  8.72759

```
