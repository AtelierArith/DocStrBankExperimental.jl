for a given [`NucleicAcidSubstitutionModel`](@ref), labels are symbols from [BioSymbols](https://github.com/BioJulia/BioSymbols.jl). For now, only ACGTs are allowed. (When fitting data, any ambiguity code in the data would be treated as missing value).

# examples

```jldoctest
julia> getlabels(JC69([0.03], false))
4-element Vector{BioSymbols.DNA}:
 DNA_A
 DNA_C
 DNA_G
 DNA_T

julia> getlabels(HKY85([.5], repeat([0.25], 4)))
4-element Vector{BioSymbols.DNA}:
 DNA_A
 DNA_C
 DNA_G
 DNA_T

```
