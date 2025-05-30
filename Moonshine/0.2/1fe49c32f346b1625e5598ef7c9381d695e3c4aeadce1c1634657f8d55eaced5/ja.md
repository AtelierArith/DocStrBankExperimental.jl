```
siblings(genealogy, v[, ωs])
siblings(genealogy, v[, ωs], buf_ptr)
```

頂点の兄弟、つまり少なくとも1人の親を共有する系譜内の他の頂点。オプションで、限界系譜に制限することができます。

割り当てを避けるために、何らかのバッファ（例えば配列）へのポインタを提供することができます。その場合、ラップされた`UnsafeArray`が返されます。

`v`が単一の兄弟を持つことが事前にわかっている場合は、[`sibling`](@ref)を代わりに使用できます。

他に[`child`](@ref)、[`dad`](@ref)、[`children`](@ref)、[`dads`](@ref)、[`descendants`](@ref)および[`ancestors`](@ref)も参照してください。

# メソッド

```julia
siblings(genealogy, v, args)
```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:868`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。
