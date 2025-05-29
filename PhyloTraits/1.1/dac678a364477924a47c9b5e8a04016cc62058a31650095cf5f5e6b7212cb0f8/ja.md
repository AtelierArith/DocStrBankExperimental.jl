与えられた [`NucleicAcidSubstitutionModel`](@ref) に対して、ラベルは [BioSymbols](https://github.com/BioJulia/BioSymbols.jl) のシンボルです。現時点では、ACGT のみが許可されています。（データをフィッティングする際、データ内のあいまいなコードは欠損値として扱われます）。

# 例

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
