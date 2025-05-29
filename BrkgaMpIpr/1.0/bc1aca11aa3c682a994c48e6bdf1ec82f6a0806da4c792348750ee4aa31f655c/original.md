```
build_brkga(problem_instance::AbstractInstance, decode_function!::Function,
            opt_sense::Sense, seed::Int64, chromosome_size::Int64,
            brkga_params::BrkgaParams, evolutionary_mechanism_on::Bool = true,
)::BrkgaData
```

Build a [`BrkgaData`](@ref) object to be used in the evolutionary and path relink procedures. Such data structure should not be changed outside the `BrkgaMpIpr` functions. This version accepts all control arguments, and it is handy for tuning purposes.

# Arguments

  * [`problem_instance::AbstractInstance`](@ref AbstractInstance): an instance to the problem to be solved.
  * `decode_function!::Function`: the decode funtion used to map chromosomes to solutions. It **must have** the following signature:

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool)::Float64
    ```

    Note that if `rewrite == false`, `decode!` cannot modify `chromosome`.
  * [`opt_sense::Sense`](@ref Sense): the optimization sense ( maximization or minimization).
  * `seed::Int64`: seed for the random number generator.
  * `chromosome_size::Int64`: number of genes in each chromosome.
  * [`brkga_params::BrkgaParams`](@ref BrkgaParams): BRKGA and IPR parameters object loaded from a configuration file or manually created. All the data is deep-copied.
  * `evolutionary_mechanism_on::Bool = true`: if false, no evolution is performed but only chromosome decoding. On each generation, all population is replaced excluding the best chromosome. Very useful to emulate a multi-start algorithm.

# Throws

  * `ArgumentError`: in several cases where the arguments or a combination of them are invalid.
