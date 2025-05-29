```
系譜の列。エッジが指定されている場合、そのエッジに接続された頂点に関連する列を返します。頂点の反復可能な集合が指定されている場合、これらの頂点に関連する列を返します。

頂点に関連する列を取得するには、[`sequence`](@ref)も参照してください。

# 実装

カスタム型は`sequences(::T)`を実装するだけで済みます。

# メソッド

```

julia sequences(genealogy, vs)

```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:147`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。

```

julia sequences(genealogy, e)

```

[`packages/Moonshine/7JVTP/src/Genealogy.jl:149`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/Genealogy.jl)で定義されています。

```

julia sequences(arg) sequences(tree)

```

[`packages/Moonshine/7JVTP/src/genealogy_common.jl:31`](file:///home/terasaki/.julia/packages/Moonshine/7JVTP/src/genealogy_common.jl)で定義されています。
```
