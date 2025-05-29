```
improper_qualified_accesses_nonrecursive(mod::Module, file=pathof(mod); skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                                         allow_internal_accesses=true)
```

A non-recursive version of [`improper_qualified_accesses`](@ref), meaning it only analyzes the module `mod` itself, not any of its submodules; see that function for details, including important caveats about stability (outputs may grow in future non-breaking releases of ExplicitImports!).

## Example

```jldoctest
julia> using ExplicitImports

julia> example_path = pkgdir(ExplicitImports, "examples", "qualified.jl");

julia> print(read(example_path, String))
module MyMod
using LinearAlgebra
# sum is in `Base`, so we shouldn't access it from LinearAlgebra:
n = LinearAlgebra.sum([1, 2, 3])
end

julia> include(example_path);

julia> row = improper_qualified_accesses_nonrecursive(MyMod, example_path)[1];

julia> (; row.name, row.accessing_from, row.whichmodule)
(name = :sum, accessing_from = LinearAlgebra, whichmodule = Base)
```
