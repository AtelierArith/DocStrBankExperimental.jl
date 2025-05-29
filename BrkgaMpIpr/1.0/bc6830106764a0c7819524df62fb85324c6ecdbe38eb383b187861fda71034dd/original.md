```
mutable struct BrkgaData
```

Represents the internal state of the BRKGA-MP-IPR algorithm.

This structure has no direct constructor and must be built using [`build_brkga`](@ref) functions. You can create multiple `BrkgaData` representing different states of the algorithm, and use them independently.

!!! warning
    This structure is **NOT INTENDED** to be used outside BRKGA functions. Ad hoc changes may lead to inadvertent results.


## Fields

  * `opt_sense`: Optimization sense (minimization = 0, maximization = 1).

  * `chromosome_size`: Number of genes in the chromosome [> 0].

  * `params`: BRKGA parameters for evolution.

  * `elite_size`: Number of elite items in the population [> 0].

  * `num_mutants`: Number of mutants introduced at each generation into the population [> 0].

  * `evolutionary_mechanism_on`: If false, no evolution is performed but only chromosome decoding. Very useful to emulate a multi-start algorithm.

  * `problem_instance`: *(Internal data)* The problem instance used by the `decode!` function to map a chromosome to a problem solution. Since `decode!` should not change this data, this attribute can be considered constant.

  * `decode!`: *(Internal data)* This is the **main decode function** called during the evolutionary process and in the path relink. It **must have** the following signature:

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool = true)::Float64
    ```

    Note that if `rewrite == false`, `decode!` must not change `chromosome`. IPR routines requires `decode!` to not change `chromosome`.

  * `rng`: *(Internal data)* The internal random generator number. DON'T USE FOR ANYTHING OUTSIDE. If you need a RNG, create a new generator.

  * `previous`: *(Internal data)* Previous population.

  * `current`: *(Internal data)* Current population.

  * `bias_function`: *(Internal data)* A unary non-increasing function such that `bias_function(::Int64 > 0)::Float64`

  * `total_bias_weight`: *(Internal data)* Holds the sum of the results of each raking given a bias function. This value is needed to normalization.

  * `shuffled_individuals`: *(Internal data)* Used to shuffled individual/chromosome indices during the mate.

  * `parents_ordered`: *(Internal data)* Defines the order of parents during the mating.

  * `initialized`: *(Internal data)* Indicates if the algorithm was proper initialized.

  * `reset_phase`: *(Internal data)* Indicates if the algorithm have been reset.
