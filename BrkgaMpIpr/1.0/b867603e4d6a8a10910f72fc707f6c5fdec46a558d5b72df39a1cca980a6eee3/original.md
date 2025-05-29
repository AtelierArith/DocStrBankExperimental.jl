```
mutable struct BrkgaParams
```

Represents the BRKGA and IPR hyper-parameters. You can load these parameters from a configuration file using [`load_configuration`](@ref) and [`build_brkga`](@ref), and write them using [`write_configuration`](@ref).

## Fields

  * `population_size`: Number of elements in the population [> 0].

  * `elite_percentage`: Percentage of individuals to become the elite set (0, 1].

  * `mutants_percentage`: Percentage of mutants to be inserted in the population

  * `num_elite_parents`: Number of elite parents for mating [> 0].

  * `total_parents`: Number of total parents for mating [> 0].

  * `bias_type`: Type of bias that will be used.

  * `num_independent_populations`: Number of independent parallel populations.

  * `pr_number_pairs`: Number of pairs of chromosomes to be tested to path relinking.

  * `pr_minimum_distance`: Mininum distance between chromosomes selected to path-relinking.

  * `pr_type`: Path relinking type.

  * `pr_selection`: Individual selection to path-relinking.

  * `alpha_block_size`: Defines the block size based on the size of the population.

  * `pr_percentage`: Percentage / path size to be computed. Value in (0, 1].
