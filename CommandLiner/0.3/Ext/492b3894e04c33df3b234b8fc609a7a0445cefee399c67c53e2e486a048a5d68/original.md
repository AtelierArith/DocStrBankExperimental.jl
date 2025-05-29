```
exty(path) ->  Symbol
```

Returns a symbol representing the path extension:

```julia
julia> exty("myfile.jpg")
:jpeg

julia> exty("myfile.jpeg")
:jpeg
```

This symbol can then be used with `hasext` to capture all extensions in an extension group, e.g., {"jpg", "jpeg", and "jpe"}.

You can use `CommandLiner.Ext.show_extgroups()` to show the extension groups, and `CommandLiner.Ext.register_extgroups(::Vector{Vector{String}})` to redefine them.

Use `ext` if you want to distinguish between special cases of empty extensions, and `exty` if not:

```julia
julia> (ext("myfile"), exty("myfile"))
(nothing, :_empty_)

julia> (ext("myfile."), exty("myfile."))
("", :_empty_)
```

You can overwrite the symbol used for missing extensions (default: `:_empty_`) via `CommandLiner.Ext.setsym_empty()`.
