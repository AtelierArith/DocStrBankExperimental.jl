```
ancestors(genealogy, v[, ωs])
ancestors(genealogy, v[, ωs], buf_ptr)
```

頂点の祖先、オプションで限られた系譜に制限される。

配列などのバッファのポインタを提供することで、アロケーションを回避できます。その場合、ラップされた`UnsafeArray`が返されます。

エッジ`e`が祖先であるかどうかを決定するために、次のルールが使用されます：

  * ωsが数値の場合、`e`の祖先区間はωsをカバーしなければなりません。
  * ωsがΩまたはΩの集合の場合、`e`の祖先区間とωsの交差は空であってはなりません。

他に[`child`](@ref)、[`dad`](@ref)、[`children`](@ref)、[`dads`](@ref)、[`sibling`](@ref)、[`siblings`](@ref)および[`descendants`](@ref)も参照してください。

# メソッド

```julia
ancestors(genealogy, v)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:777`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。

```julia
ancestors(genealogy, v, ω)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:810`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。
