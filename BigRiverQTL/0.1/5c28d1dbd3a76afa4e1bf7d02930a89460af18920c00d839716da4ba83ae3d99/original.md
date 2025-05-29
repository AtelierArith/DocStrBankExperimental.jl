```
encode_genotype(geno_dict::Dict{String, Any}, geno_val::AbstractArray) -> Matrix
```

Encode a matrix of genotype values using a dictionary of predefined mappings.

# Arguments

  * `geno_dict::Dict{String, Any}`: A dictionary mapping genotype strings to integer codes.
  * `geno_val::AbstractArray`: An array of genotype strings to be encoded.

# Returns

  * `Matrix{Union{Missing, Int64}}` or `Matrix{Int64}`: A matrix of the same dimensions as

`geno_val` where each genotype string is replaced by its corresponding integer code.  Genotypes not found in `geno_dict` are encoded as `missing`.

# Description

The function first copies the provided `geno_dict` to preserve the original. It then identifies  any genotypes in `geno_val` that are not already present in the dictionary. A warning is issued  for these missing genotypes, and they are added to the dictionary with a mapping to `missing`.

Each element in the input `geno_val` is replaced in the `encoded_val` matrix by its corresponding  integer code from `geno_dict`, handling both existing and newly added genotype mappings.

# Examples

```julia
geno_dict = Dict{String, Any}("AA" => 1, "AB" => 2, "BB" => 3)
geno_val = ["AA", "AB", "BB", "BC"]
encoded_matrix = encode_genotype(geno_dict, geno_val)
println(encoded_matrix)
```
