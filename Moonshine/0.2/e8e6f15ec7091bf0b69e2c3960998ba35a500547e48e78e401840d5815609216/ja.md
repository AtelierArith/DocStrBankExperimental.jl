```
children(genealogy, v[, ωs])
```

頂点の子供。オプションで、限界系譜に制限される場合があります。`v`が単一の子供を持つことが事前にわかっている場合は、[̀̀`child`](@ref)を代わりに使用してください。

エッジ`e`が祖先であるかどうかを判断するために、以下のルールが使用されます：

  * ωsが数値の場合、`e`の祖先区間はωsをカバーしなければなりません。
  * ωsがΩまたはΩの集合の場合、`e`の祖先区間とωsの交差は空であってはなりません。

!!! danger
    基本の隣接リストへの**参照**を返します。触らないでください！


他に[`dad`](@ref)、[`dads`](@ref)、[`sibling`](@ref)、[`siblings`](@ref)、[`descendants`](@ref)、[`ancestors`](@ref)を参照してください。

# メソッド

```julia
children(arg, v, ωs)
children(arg, v, ωs)
children(arg, v, ωs)
```

[`packages/Moonshine/7JVTP/src/Arg/Arg.jl:123`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Arg.jl)で定義されています。

```julia
children(genealogy, v)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:700`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。
