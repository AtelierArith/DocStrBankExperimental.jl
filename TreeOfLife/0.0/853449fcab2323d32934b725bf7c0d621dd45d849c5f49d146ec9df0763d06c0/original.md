```
rename!(tree::Tree, 
	oldtonew::Dict{<:AbstractString,<:AbstractString}
```

Rename nodes of the tree in place by a mapping from old names to new names.  Specifically, nodes with empty names remain.
