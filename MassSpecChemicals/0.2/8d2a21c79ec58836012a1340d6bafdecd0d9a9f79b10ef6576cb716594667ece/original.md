```
isotopicabundance(chemical::AbstractChemical; ignore_isotopes = false)
isotopicabundance(formula::AbstractString; ignore_isotopes = false)
isotopicabundance(elements::Union{<: Vector, Dictionary}; ignore_isotopes = false)
```

Compute isotopic abundance of `chemical`, `formula`, vector of element-number pairs or dictionary mapping element to number. 
