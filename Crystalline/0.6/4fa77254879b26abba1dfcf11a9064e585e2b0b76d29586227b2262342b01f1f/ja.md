```
generators(num::Integer, ::Type{SubperiodicGroup{D,P}})  -->  ::Vector{SymOperation{D}}
```

埋め込み次元 `D` と周期次元 `P` のサブ周期群 `num` の標準的な生成元のセットを返します。詳細は [`subperiodicgroup`](@ref) を参照してください。

また、[`generators(::Integer, ::Type{SpaceGroup})`](@ref) とその情報も参照してください。

## 例

```jldoctest
julia> generators(7, SubperiodicGroup{2, 1})
2-element Vector{SymOperation{2}}:
 2
 {m₁₀|½,0}
```

## データソース

この関数によって返される生成元は、元々 [Bilbao Crystallographic Database, SUBPERIODIC GENPOS](https://www.cryst.ehu.es/subperiodic/get_sub_gen.html) から取得されました。
