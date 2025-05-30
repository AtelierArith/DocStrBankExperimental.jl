```
runtests(dir::String ;
         failfast::Bool = false,
         targets::Union{AbstractString, Vector{<: AbstractString}} = String[],
         skip::Union{Vector{Any}, Vector{<: AbstractString}} = String[],
         testset::Union{Nothing, AbstractString, Vector{<: AbstractString}, Regex, Base.Callable} = nothing,
         context::Union{Nothing, Module} = nothing,
         enable_distributed::Bool = true,
         node1::Union{Vector{Any}, Vector{<: AbstractString}} = String[],
         verbose::Bool = true)::Total
```

run the test files from the specific directory.

  * `dir`: the root directory to traverse.
  * `failfast`: aborting on the first failure. be overridden when the `ENV` variable `JULIA_TEST_FAILFAST` has set.
  * `targets`: filter targets and start. ``(space) separated `String` or a `Vector{String}`. be overridden when `ARGS` are not empty.
  * `skip`: files or directories to skip. be overridden when the `ENV` variable `JIVE_SKIP` has set. `,`(comma) separated.
  * `testset`: filter testset. default is `nothing`.
  * `context`: module that to be used in `Base.include`. `nothing` means to be safe that using anonymous module for every test file.
  * `enable_distributed`: option for distributed. be overridden when the `ENV` variable `JIVE_PROCS` has set.
  * `node1`: run on node 1 during for the distributed tests.
  * `verbose`: print details of test execution
