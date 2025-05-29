```
Mutagenesis(; split=:train, dir=nothing)
Mutagenesis(split; dir=nothing)
```

The `Mutagenesis` dataset comprises 188 molecules trialed for mutagenicity on Salmonella typhimurium, available from  [relational.fit.cvut.cz](https://relational.fit.cvut.cz/dataset/Mutagenesis) and  [CTUAvastLab/datasets](https://github.com/CTUAvastLab/datasets/tree/main/mutagenesis).

Set `split` to `:train`, `:val`, `:test`, or `:all`, to select the training,  validation, test partition respectively or the whole dataset. The `indexes` field in the result contains the indexes of the partition in the full dataset.

Website: https://relational.fit.cvut.cz/dataset/Mutagenesis License: CC0

```julia-repl
julia> using MLDatasets: Mutagenesis

julia> dataset = Mutagenesis(:train)
Mutagenesis dataset:
  split : train
  indexes : 100-element Vector{Int64}
  features : 100-element Vector{Dict{Symbol, Any}}
  targets : 100-element Vector{Int64}

julia> dataset[1].features
Dict{Symbol, Any} with 5 entries:
  :lumo  => -1.246
  :inda  => 0
  :logp  => 4.23
  :ind1  => 1
  :atoms => Dict{Symbol, Any}[Dict(:element=>"c", :bonds=>Dict{Symbol, Any}[Dict(:element=>"c", :bond_type=>7, :charge=>-0.117, :atom_type=>22), Dict(:element=>"h", :bond_type=>1, :charge=>0.142, :atom_type=>3)…

julia> dataset[1].targets
1

julia> dataset = Mutagenesis(:all)
Mutagenesis dataset:
  split : all
  indexes : 188-element Vector{Int64}
  features : 188-element Vector{Dict{Symbol, Any}}
  targets : 188-element Vector{Int64}
```
