```
struct GlobalRel <: AbstractRelation end;
const globalrel  = GlobalRel();
```

グローバル関係のシングルトン型。これは、ある世界がフレーム内の他のすべての世界にアクセスするための二項関係です。この関係は対称的、反射的、かつ推移的でもあります。

# 例

```julia-repl
julia> syntaxstring(SoleLogics.globalrel)
"G"

julia> SoleLogics.converse(globalrel)
GlobalRel()
```

関連項目としては [`identityrel`](@ref), [`AbstractRelation`](@ref), [`AbstractWorld`](@ref), [`AbstractFrame`](@ref). [`AbstractKripkeStructure`](@ref) があります。
