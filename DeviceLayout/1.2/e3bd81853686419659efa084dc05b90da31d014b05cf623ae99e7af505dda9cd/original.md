```
uniquename(str, dlm="\$"; modify_first=false, counter=GLOBAL_NAME_COUNTER)
```

Given string input `str` for the `n`th time, return `str * dlm * string(n)`.

If `str` is already formatted as `str0 * dlm * n`, where `n` is an integer, then `str0` will be used with the larger of `n` and the number of times `str0` has been counted plus one.

If `modify_first` is `false`, then `str` will be returned the first time `uniquename(str, dlm; modify_first=false)` is called.

Useful if programmatically making Cells and all of them will eventually be saved into a GDSII file.

The uniqueness is expected on a per-Julia session basis or until [`reset_uniquename!`](@ref) is called, so if you load an existing GDSII file and try to save unique cells on top of that you may get an unlucky clash. Calling `uniquename` on all loaded `Cell` names will effectively "register" them, making subsequent `uniquename` calls aware of them.

# Example

```jldoctest
julia> reset_uniquename!();

julia> uniquename("name"; modify_first=true)
"name\$1"

julia> uniquename("name\$4")
"name\$4"

julia> uniquename("name\$3")
"name\$5"

julia> uniquename("name")
"name\$6"
```

`counter` is the `Dict{String,Int}` that counts how many times each name has been seen. The default is a global counter that persists until the end of the Julia session or until [`reset_uniquename!`](@ref) is called.
