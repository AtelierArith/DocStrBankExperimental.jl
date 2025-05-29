```
descendants(genealogy, v[, ωs])
descendants(genealogy, v[, ωs], buf_ptr)
```

頂点の子孫、オプションで限られた系譜に制限される。

配列などのバッファのポインタを提供することで、アロケーションを避けることができます。その場合、ラップされた`UnsafeArray`が返されます。

エッジ`e`が祖先であるかどうかを決定するために使用されるルールは次のとおりです：

  * ωsが数値の場合、`e`の祖先区間はωsをカバーしなければなりません。
  * ωsがΩまたはΩの集合である場合、`e`の祖先区間とωsの交差は空であってはなりません。

[`child`](@ref)、[`dad`](@ref)、[`children`](@ref)、[`dads`](@ref)、[`sibling`](@ref)、[`siblings`](@ref)、および[`ancestors`](@ref)も参照してください。

# メソッド

```julia
descendants(genealogy, v)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:777`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。

```julia
descendants(genealogy, v, ω)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:810`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。
