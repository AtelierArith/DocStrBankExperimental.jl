```
build_brkga(problem_instance, decode_function!, opt_sense, seed,
    chromosome_size, configuration_file,
    evolutionary_mechanism_on)::Tuple{BrkgaData, ExternalControlParams}
```

Build a [`BrkgaData`](@ref) object to be used in the evolutionary and path relink procedures, and a [`ExternalControlParams`](@ref) that holds additional control parameters. Note that [`BrkgaData`](@ref) should not be changed outside the `BrkgaMpIpr` functions. This version reads most of the parameters from a configuration file.

# Arguments

  * [`problem_instance::AbstractInstance`](@ref AbstractInstance): an instance to the problem to be solved.
  * `decode_function!::Function`: the decode funtion used to map chromosomes to solutions. It **must have** the following signature:

    ```julia
    decode!(chromosome::Array{Float64, 1},
            problem_instance::AbstractInstance,
            rewrite::Bool = true)::Float64
    ```

    Note that if `rewrite == false`, `decode!` cannot modify `chromosome`.
  * [`opt_sense::Sense`](@ref Sense): the optimization sense ( maximization or minimization).
  * `seed::Int64`: seed for the random number generator.
  * `chromosome_size::Int64`: number of genes in each chromosome..
  * `configuration_file::String`:  text file with the BRKGA parameters. An example can be found at <a href="example.conf">example.conf</a>. Note that the content after "#" is considered comments and it is ignored.
  * `evolutionary_mechanism_on::Bool = true`: if false, no evolution is performed but only chromosome decoding. On each generation, all population is replaced excluding the best chromosome. Very useful to emulate a multi-start algorithm.

# Throws

  * `LoadError`: in cases of the file is an invalid configuration file, parameters are missing, or parameters are ill-formatted.
  * `SystemError`: in case the configuration files cannot be openned.
