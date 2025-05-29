```
run_igblast(
    igblast_type::Type{T},
    query_file::String,
    v_database::String,
    d_database::String,
    j_database::String,
    aux_file::String,
    output_file::String,
    num_threads::Int = Base.Threads.nthreads();
    outfmt::Int = 19,
    additional_params::Dict{String, Any} = Dict()
) where T <: AbstractIgBLAST
```

Run IgBLAST with the specified parameters.

Required parameters:

  * `igblast_type`: Type of IgBLAST to run (IgBLASTn or IgBLASTp)
  * `query_file`: Path to the input query file
  * `v_database`: Path to the V gene database
  * `d_database`: Path to the D gene database
  * `j_database`: Path to the J gene database
  * `aux_file`: Path to the auxiliary file
  * `output_file`: Path for the output file

Optional parameters:

  * `num_threads`: Number of threads to use (default: all available threads)
  * `outfmt`: Output format (default: 19 for AIRR format)
  * `additional_params`: Dictionary of additional IgBLAST parameters

Example:

```julia
run_igblast(IgBLASTn, "query.fasta", "V.fasta", "D.fasta", "J.fasta", "aux.txt", "output.txt",
            additional_params = Dict(
                "organism" => "human",
                "domain_system" => "imgt"
            ))
```
