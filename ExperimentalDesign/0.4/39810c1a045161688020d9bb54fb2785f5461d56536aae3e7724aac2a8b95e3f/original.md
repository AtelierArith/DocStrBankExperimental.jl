```julia
kl_exchange(
    formula::StatsModels.FormulaTerm,
    candidate_set::DataFrames.DataFrame;
    tolerance,
    seed_design_size,
    max_iterations,
    experiments,
    design_k,
    candidates_l
)

```

Builds optimum designs using the KL exchange algorithm, as described by Atkinson *et al.*.   The ideia is  to iteratively swap  $K$ design elements  with $L$ candidate elements,  in order to  *maximize* an optimality  criterion.  Although any criteria based  on information matrices could be used  here, the KL exchange algorithm     leverages    determinant     properties     to    optimize     the [`d_criterion`](@ref).

> Atkinson, A., Donev, A., & Tobias, R. (2007). Optimum experimental designs, with SAS (Vol. 34). Oxford University Press, Chapter 12.


```julia
julia> candidates = FullFactorial(fill([-1, 0, 1], 5));

julia> candidates_formula = ConstantTerm(0) ~ sum(Term.(Symbol.(names(candidates.matrix))));

julia> candidates_formula = FormulaTerm(candidates_formula.lhs,
                                        candidates_formula.rhs +
                                        (@formula 0 ~ factor3 ^ 2).rhs);

julia> selected_rows = kl_exchange(candidates_formula,
                                   candidates.matrix,
                                   seed_design_size = 2,
                                   experiments = 11,
                                   design_k = 11,
                                   candidates_l = size(candidates.matrix, 1) - 11);

julia> d_criterion(selected_rows)
0.730476820204009

julia> candidates.matrix[selected_rows.indices[1], :]
11×5 DataFrames.DataFrame
│ Row │ factor1 │ factor2 │ factor3 │ factor4 │ factor5 │
│     │ Int64   │ Int64   │ Int64   │ Int64   │ Int64   │
├─────┼─────────┼─────────┼─────────┼─────────┼─────────┤
│ 1   │ -1      │ 1       │ -1      │ 1       │ 1       │
│ 2   │ 1       │ -1      │ 1       │ 1       │ 1       │
│ 3   │ 1       │ 1       │ 0       │ -1      │ 1       │
│ 4   │ -1      │ 1       │ 1       │ -1      │ 1       │
│ 5   │ -1      │ -1      │ 0       │ 1       │ 1       │
│ 6   │ 1       │ 1       │ 1       │ 1       │ -1      │
│ 7   │ -1      │ -1      │ 1       │ -1      │ -1      │
│ 8   │ 1       │ -1      │ 0       │ 1       │ -1      │
│ 9   │ -1      │ 1       │ -1      │ 1       │ -1      │
│ 10  │ -1      │ 1       │ 0       │ -1      │ -1      │
│ 11  │ 1       │ -1      │ -1      │ -1      │ -1      │
```

```julia
julia> n_candidates = 3000;

julia> n_factors = 30;

julia> design_generator = DesignDistribution(Uniform(0, 1), n_factors);

julia> candidates = rand(design_generator, n_candidates);

julia> selected_rows = kl_exchange(candidates.formula,
                                   candidates.matrix,
                                   experiments = n_factors + 2,
                                   design_k = n_factors,
                                   candidates_l = round(Int, (n_candidates - n_factors) / 2));

julia> d_criterion(selected_rows)
0.07904918814259465

julia> candidates.matrix[selected_rows.indices[1], :]
32×30 DataFrame. Omitted printing of 24 columns
│ Row │ factor1    │ factor2   │ factor3   │ factor4   │ factor5   │ factor6   │
│     │ Float64    │ Float64   │ Float64   │ Float64   │ Float64   │ Float64   │
├─────┼────────────┼───────────┼───────────┼───────────┼───────────┼───────────┤
│ 1   │ 0.832487   │ 0.875035  │ 0.433788  │ 0.805738  │ 0.481517  │ 0.382364  │
│ 2   │ 0.761498   │ 0.0398811 │ 0.998741  │ 0.632286  │ 0.29121   │ 0.55497   │
│ 3   │ 0.639793   │ 0.49432   │ 0.678795  │ 0.685274  │ 0.269203  │ 0.896397  │
│ 4   │ 0.00370418 │ 0.5139    │ 0.0630861 │ 0.175531  │ 0.570244  │ 0.60512   │
│ 5   │ 0.698514   │ 0.207593  │ 0.766977  │ 0.0719112 │ 0.665055  │ 0.499193  │
│ 6   │ 0.412744   │ 0.785263  │ 0.432861  │ 0.909976  │ 0.642545  │ 0.832013  │
│ 7   │ 0.353518   │ 0.116685  │ 0.140352  │ 0.929095  │ 0.0484366 │ 0.838524  │
⋮
│ 25  │ 0.577343   │ 0.790529  │ 0.763994  │ 0.548131  │ 0.402066  │ 0.293336  │
│ 26  │ 0.0941214  │ 0.52891   │ 0.293733  │ 0.92224   │ 0.982713  │ 0.929744  │
│ 27  │ 0.0256128  │ 0.723072  │ 0.23927   │ 0.993221  │ 0.521335  │ 0.407319  │
│ 28  │ 0.221631   │ 0.375189  │ 0.67251   │ 0.658613  │ 0.272448  │ 0.230501  │
│ 29  │ 0.843885   │ 0.375497  │ 0.116069  │ 0.989937  │ 0.935444  │ 0.0466424 │
│ 30  │ 0.181611   │ 0.956062  │ 0.98997   │ 0.80352   │ 0.994557  │ 0.203797  │
│ 31  │ 0.738407   │ 0.25753   │ 0.929704  │ 0.407498  │ 0.0934688 │ 0.99359   │
│ 32  │ 0.228975   │ 0.81272   │ 0.803107  │ 0.931826  │ 0.598371  │ 0.588823  │
```
