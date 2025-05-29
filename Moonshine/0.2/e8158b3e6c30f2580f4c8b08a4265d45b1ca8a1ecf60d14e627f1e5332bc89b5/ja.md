```
dads(genealogy, v[, ωs])
```

頂点の親。オプションで、限界系譜に制限できます。`v`が単一の父親を持つことが事前にわかっている場合は、[̀̀`dad`](@ref)を代わりに使用してください。

エッジ`e`が祖先であるかどうかを判断するために使用されるルールは次のとおりです。

  * ωsが数値の場合、`e`の祖先区間はωsをカバーしなければなりません。
  * ωsがΩまたはΩの集合である場合、`e`の祖先区間とωsの交差は空であってはなりません。

!!! danger
    基本の隣接リストへの**参照**を返します。触らないでください！


他に[`child`](@ref)、[`children`](@ref)、[`sibling`](@ref)、[`siblings`](@ref)、[`descendants`](@ref)、[`ancestors`](@ref)も参照してください。

# メソッド

```julia
dads(arg, v, ωs)
dads(arg, v, ωs)
dads(arg, v, ωs)
```

[`packages/Moonshine/7JVTP/src/Arg/Arg.jl:123`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl)で定義されています。

```julia
dads(genealogy, v)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:700`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。
