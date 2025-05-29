```
eachmodel(atoms::AbstractVector{<:Atom})
```

Iterator for the models of a selection.

### Example

Here we show how to iterate over the models of a PDB file, annotate  the index of the first atom of each model, and collect all models.

```jldoctest
julia> using PDBTools

julia> ats = wget("8S8N");

julia> models = eachmodel(ats)
 Model iterator with length = 11

julia> first_atom = Atom[]
       for model in models
           push!(first_atom, model[1])
       end
       @show index.(first_atom);
index.(first_atom) = Int32[1, 235, 469, 703, 937, 1171, 1405, 1639, 1873, 2107, 2341]

julia> collect(models)
11-element Vector{Model}[
    1-(234 atoms))
    2-(234 atoms))
    ⋮
    10-(234 atoms))
    11-(234 atoms))
]
```
