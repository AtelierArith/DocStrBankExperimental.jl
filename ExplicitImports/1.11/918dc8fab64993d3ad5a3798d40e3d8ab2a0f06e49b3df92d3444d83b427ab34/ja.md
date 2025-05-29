```
improper_qualified_accesses_nonrecursive(mod::Module, file=pathof(mod); skip=(Base => Core,
                                                                     Compat => Base,
                                                                     Compat => Core),
                                         allow_internal_accesses=true)
```

[`improper_qualified_accesses`](@ref) の非再帰バージョンであり、モジュール `mod` 自体のみを分析し、そのサブモジュールは分析しません。詳細についてはその関数を参照してください。安定性に関する重要な注意事項（出力は将来の非破壊的リリースの ExplicitImports! で増加する可能性があります）も含まれています。

## 例

```jldoctest
julia> using ExplicitImports

julia> example_path = pkgdir(ExplicitImports, "examples", "qualified.jl");

julia> print(read(example_path, String))
module MyMod
using LinearAlgebra
# sum は `Base` にあるので、LinearAlgebra からアクセスすべきではありません:
n = LinearAlgebra.sum([1, 2, 3])
end

julia> include(example_path);

julia> row = improper_qualified_accesses_nonrecursive(MyMod, example_path)[1];

julia> (; row.name, row.accessing_from, row.whichmodule)
(name = :sum, accessing_from = LinearAlgebra, whichmodule = Base)
```
