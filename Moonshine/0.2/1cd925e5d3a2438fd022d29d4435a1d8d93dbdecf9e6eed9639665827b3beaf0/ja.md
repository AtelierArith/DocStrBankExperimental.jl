```julia
sibling(genealogy, v)

```

頂点の兄弟、つまり同じ親を持つ系譜の別の頂点です。このメソッドを使用するのは、`v` に単一の兄弟がいることがわかっている場合にのみ意味があります。そうでない場合は、[`siblings`](@ref) を使用してください。

また、[`child`](@ref)、[`dad`](@ref)、[`children`](@ref)、[`dads`](@ref)、[`descendants`](@ref)、および [`ancestors`](@ref) も参照してください。
