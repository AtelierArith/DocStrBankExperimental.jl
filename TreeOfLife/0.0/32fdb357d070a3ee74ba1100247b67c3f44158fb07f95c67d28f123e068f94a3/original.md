```
rename(oldtree::AbstractTree, 
	oldtonew::Dict{<:AbstractString,<:AbstractString}
```

Create a new tree whose nodes are respectively renamed from the `oldtree` by  a mapping from old names to new names. Specifically, nodes with empty names  remain.
