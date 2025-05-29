```
get_value(l::LoopCategory, k::Dict{Symbol, V}, name::Symbol)
```

Return the value of `name` where the key values are given by the contents of `k` as Symbols. This form of the method will treat child category object names as members of parent categories, so for example u*11 belongs to both atom*site*aniso and atom*site if atom*site*aniso is a child category of atom_site. Linked key data names are treated in the same way.
