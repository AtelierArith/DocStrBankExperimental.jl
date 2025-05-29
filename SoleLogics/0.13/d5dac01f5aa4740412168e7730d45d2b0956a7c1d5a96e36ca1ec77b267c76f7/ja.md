```
struct IdentityRel <: AbstractRelation end;
const identityrel   = IdentityRel();
```

同一性関係のシングルトン型。この関係は、世界が自分自身にアクセスするための二項関係です。この関係は対称的、反射的、かつ推移的でもあります。

# 例

```julia-repl
julia> syntaxstring(SoleLogics.identityrel)
"="

julia> SoleLogics.converse(identityrel)
IdentityRel()
```

参照: [`globalrel`](@ref), [`AbstractRelation`](@ref), [`AbstractWorld`](@ref), [`AbstractFrame`](@ref). [`AbstractKripkeStructure`](@ref),
