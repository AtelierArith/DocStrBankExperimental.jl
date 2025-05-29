```
@scachejld [[type] cache_dir] function_call
```

Cache the result of `function_call` in directory `cache_dir` prefixing the saved file with `type`.

This macro uses `JLD2` `@save` and `@load` macros to save and load cached files so it is slower and less memory efficent than [`@scache`](@ref) macro which uses `serialize` which, on the other hand, is less portable between different julia versions.

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

julia> @scachejld "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:56:09 ] Computing cute-cube...
● [ 2022-12-09 15:56:09 ] Computed cute-cube in 0.0 seconds (00:00:00)
● [ 2022-12-09 15:56:09 ] Saving cute-cube to file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld[.tmp]...
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

julia> @scachejld "cute-cube" "./" fill(0, 3, 3, 3)
● [ 2022-12-09 15:56:19 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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
-rw-r--r--. 1 user user 1000  9 dic 15.56 cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld

```

Expressions in function argument will be computed as first step so the cached file will be loaded even if the arguments are different but will evaluate to the same result.

```julia-repl
julia> @scachejld "cute-cube" "./" fill(0, 3, round(Int64, 1.5 * 2), 3)
● [ 2022-12-09 15:59:13 ] Loading cute-cube from file ./cute-cube_4bbf9c2851f2c2b3954448f1a8085f6e3d40085add71f19640343885a8b7bd6a.jld...
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
