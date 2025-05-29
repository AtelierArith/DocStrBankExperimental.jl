```
select_with_vmd(inputfile::String, selection::String; vmd="vmd", srcload=nothing)
select_with_vmd(atoms::AbstractVector{<:Atom}, selection::String; vmd="vmd", srcload=nothing)
```

Select atoms using vmd selection syntax, with vmd in background. The input can be a file or a list of atoms.

Returns a tuple with list of index (one-based) and atom names of the selection.

Function to return the selection from a input file (topology, coordinates, etc),  by calling VMD in the background.

The `srcload` argument can be used to load a list of scripts before loading the input file, for example with macros to define custom selection keywords.
