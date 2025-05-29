```
@scache [[type] cache_dir] function_call
```

Cache the result of `function_call` in directory `cache_dir` prefixing the saved file with `type`.

This macro uses `Serialize` `serialize` and `deserialize` functions to save and load cached files so it is faster and more memory efficent than [`@scachejld`](@ref) macro which uses `JLD2` which, on the other hand, is more portable between different julia versions.

!!! note
    The file extension will be `.jld` when using both [`@scache`](@ref) and [`@scachejld`](@ref).


!!! note
    If `type` is omitted the function name will be used as `type`.


!!! note
    If `cache_dir` is omitted the value set in filed `cache_dir` in [`SimpleCachingSettings`](@ref) will be used.


## Examples

```julia-repl
julia> using SimpleCaching

julia> SimpleCaching.settings.log = true;

julia> @scache "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:39:42 ] Computing cute-cube...
● [ 2022-12-09 15:39:42 ] Computed cute-cube in 0.009 seconds (00:00:00)
● [ 2022-12-09 15:39:44 ] Saving cute-cube to file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld[.tmp]...
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

julia> @scache "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:39:56 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

shell> ls -l cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld
-rw-r--r--. 1 user user 232  9 dic 15.39 cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld

```

Expressions in function argument will be computed as first step so the cached file will be loaded even if the arguments are different but will evaluate to the same result.

```julia-repl
julia> @scache "cute-cube" "./" fill(0, 3, parse(Int, "3"), 3)
● [ 2022-12-09 09:41:54 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
3×3×3 Array{Int64, 3}:
[:, :, 1] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 2] =
 0  0  0
 0  0  0
 0  0  0

[:, :, 3] =
 0  0  0
 0  0  0
 0  0  0

```
