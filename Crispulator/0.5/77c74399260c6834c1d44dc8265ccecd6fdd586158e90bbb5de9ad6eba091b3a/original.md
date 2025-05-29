```julia
select(
    setup,
    initial_cells,
    initial_cell_phenotypes,
    guides
)

```

Given a population `initial_cells` with `initial_cell_phenotypes`, this function models the selection step of a [GrowthScreen](@ref). Cells are allowed to double according to their growth phenotype and then the population is subsampled to simulate passaging to maintain the `bottleneck_representation` as defined in `setup`. The number of doublings + subsamplings are controlled by the `num_bottlenecks` parameter in `setup`.

So for a screen where there are three bottlenecks and the `length(initial_cells) == bottleneck_representation` then we would expect the following behavior:

```
           Cell population
```

┌────────────────────────────────────────┐ 2 │           .-           .r|          ..|│   │         r*`|         _-' |        .r/ |│   │       ."   |       .*    |      .r'   |│   │    .-"      |    ,"`|    ,/'     |│   │  _-`        | .-/        |  .*`       |│ 1 │_*           Lr'          |r/          |│   └────────────────────────────────────────┘    0                                      3                  Bottleneck #

If the coverage of the library by `initial_cells` is less than the `bottleneck_representation` than the population will be allowed to double until passaging is needed or the `num_bottlenecks` is hit, which ever comes first.
