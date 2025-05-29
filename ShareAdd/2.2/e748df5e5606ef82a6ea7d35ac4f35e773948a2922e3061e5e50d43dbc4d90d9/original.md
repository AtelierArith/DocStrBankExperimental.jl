```
info(nms::Union{Nothing, String, Vector{String}} = nothing; 
    by_env=true, listing=nothing, std_lib=false, upgradable=false, disp_rslt=true, ret_rslt=false)
```

Prints out and/or returns information about shared environments.

# Argument

  * `nms`: Name(s) of package(s) or environment(s) to return the information on. Environment names must start with "@". Package and env names cannot be provided together in one array.

# Keyword arguments

  * `by_env=true`: whether to print out results as a `Dict` of pairs like `@env => [pkg1, ...]`, or `pkg => [@env1, ...]`. Has no effect on returned (if any) results.
  * `listing=nothing`: this kwarg can be `nothing`, `:envs`, or `:pkgs`. If one of these two `Symbol`s is provided, the result is printed as a vector of envs or pkgs, resp. In this case `by_env` is ignored. Has no effect on returned (if any) results
  * `upgradable=false`: if true, all other kwargs will be ignored, and only upgradable packages with installed vs. most recent versions will be printed, ordered by environment.
  * `disp_rslt=true`: whether to print out results.
  * `ret_rslt=false`: whether the function returns anything. If set to `true`, it returns a NamedTuple `(; env_dict, pkg_dict, envs, pkgs, absent)`, where the two first elements are  `Dict`s with keywords correspondingly by env or by pkg; `envs` and `pkgs` are vectors of  respective elements, and `absent` are those names provided through the `nms` argument, which  are not contained in the shared envs. Names of envs in the returned data are without leading "@".

This function is public, but **not exported**, as to avoid possible name conflicts. 

# Examples

```julia-repl
julia> ShareAdd.info(["BenchmarkTools", "Chairmarks"])
The following packages are not in any shared env:
    ["Chairmarks"]

Found pkgs/envs:
  @BenchmarkTools
   => ["BenchmarkTools"]
  @Tools
   => ["BenchmarkTools"]

julia> ShareAdd.info(["DataFrames", "CSV"]; by_env=false)
  CSV
   => ["@DataFrames"]
  DataFrames
   => ["@DataFrames"]

julia> ShareAdd.info("StaticArrays"; upgradable=true)
  @StaticArrays
    StaticArrays: 1.9.8 --> 1.9.10   
```
