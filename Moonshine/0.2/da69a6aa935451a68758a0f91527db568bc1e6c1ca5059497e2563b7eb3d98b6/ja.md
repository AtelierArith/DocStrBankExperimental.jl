```
ancestors(genealogy, v[, ωs])
ancestors(genealogy, v[, ωs], buf_ptr)
```

頂点の祖先、オプションで限られた系譜に制限される。

配列などのバッファのポインタを提供することで、アロケーションを避けることができます。その場合、ラップされた `UnsafeArray` が返されます。

エッジ `e` が祖先であるかどうかを決定するために次のルールが使用されます：

  * ωs が数値の場合、`e` の祖先区間は ωs をカバーしなければなりません。
  * ωs が Ω または Ω の集合の場合、`e` の祖先区間と ωs の交差は空であってはなりません。

他にも [`child`](@ref), [`dad`](@ref), [`children`](@ref), [`dads`](@ref), [`sibling`](@ref), [`siblings`](@ref) および [`descendants`](@ref) を参照してください。

# メソッド

```julia
ancestors(genealogy, v)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:777`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。

```julia
ancestors(genealogy, v, ω)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:810`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl) で定義されています。
