```julia
read_evidence_file(
    evidence_filepath::AbstractString
) -> Tuple{Vector{Int64}, Vector{Int64}}

```

Return the observed variables and values in `evidence_filepath`. If the passed file path is an empty string, return empty vectors.

The UAI file formats are defined in: https://uaicompetition.github.io/uci-2022/file-formats/
