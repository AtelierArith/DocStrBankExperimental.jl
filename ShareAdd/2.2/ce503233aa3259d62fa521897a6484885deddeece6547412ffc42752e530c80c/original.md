```
delete(nms::Union{String, Vector{String}}; inall=ASKING, force = ASKING) -> nothing
delete(nm::AbstractString; inall=ASKING, force = ASKING) -> nothing
delete(p::Pair{<:AbstractString, <:AbstractString}; force = ASKING) -> nothing
```

Deletes shared envs, or packages therein.

If the provided argument is name(s) of shared environment(s), as specified by leading "@" in the names(s): then  deletes the shared environment(s) by erasing their directories.

Otherwise, the provided name(s) are considered package names: then for each package `pkg` deletes it from it's shared environment(s).  Afterwards deletes the environment if it left empty after package deletion.

You can also specify both the env and the package in the form  `"@Foo" => "bar"`

# Keyword arguments

Both kwargs accept any integer types, including Bool, as well as enum [`SkipAskForceEnum`](@ref) with integer values [-1=>SKIPPING, 0=>ASKING, 1=>FORCING]. If Bool is used,  `false` is equivalent to `ASKING`, and `true` to `FORCING`

  * `inall=ASKING`: If set to `FORCING`, would delete package from multiple environments, whereas with `SKIPPING`, it will skip without asking. Has no effect if provided `nms` is/are env name(s).
  * `force=ASKING`: If set to `FORCING`, would delete the env even if the env is currently in `LOAD_PATH`, and remove a package even if it is loaded.

# Examples

```julia-repl
julia> ShareAdd.delete("@TrialPackages")
julia> ShareAdd.delete(["UnusedPkg", "UselessPkg"]; inall=true)
julia> ShareAdd.delete("@Foo" => "bar")
```

This function is public, not exported.
