```
add_ct(data::Dict{String,Any}, element::String, id::String, n_p::Number, n_s::Number;kwargs...)
```

Function to add current transformer to circuit. Inputs 4 if adding first CT, 5 otherwise:     (1) data(Dictionary): Result from parse*file(). Circuit information     (2) element(String): Element or line that CT is being added to     (3) id(String): Optional. For multiple CT on the same line. If not used overwrites previously defined CT1     (4) n*p(Number): Primary . Would be the number of  of the relay side of transformer     (5) n_s(Number): Secondary . Number of  on line side     (6) kwargs: Any other information user wants to add. Not used by anything.
