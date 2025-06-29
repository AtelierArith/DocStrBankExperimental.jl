```
treemap(f, node)
```

ルート `node` を持つ木のすべてのノードに関数 `f` を適用します。ここで、`f` は `(v, ch)` を返す関数であり、`v` はノードの新しい値（すなわち [`nodevalue`](@ref) によって返されるもの）で、`ch` はノードの新しい子ノードです。`f` は再帰的に呼び出されるため、親ノードのために `f` が返すすべての子ノードは再び各子ノードに対して呼び出されます。これは、木の構造を維持しつつ新しい値にマッピングするためには、`f = node -> (g(node), children(node))` のように、ノードの値を返す関数 `g` を定義する必要があることを意味します。

出力木のノードはすべて、返された値をラップする [`MapNode`](@ref) オブジェクトによって表されます。これは、出力タイプが任意の木のトポロジーを記述できることを保証するために必要です。

ほとんどの一般的なケースでは、木のノードはその接続性に依存する型であり、関数 `f` はこれを考慮する必要があります。たとえば、木 `[1, [2, 3]]` は整数の葉を含みますが、2つの `Vector` ノードを持っています。したがって、`treemap(f, [1, [2,3]])` の `f` は、`Int` または `Vector` のいずれかに対して有効な関数でなければなりません。あるいは、葉のみに操作を行うには `map(𝒻, Leaves(itr))` を使用します。

`f` を記述するのは非常に簡単ですが、`treemap` がスタックオーバーフローを引き起こすことがあります。これを避けるために、`f` が最終的に終了すること、すなわち時々空の `children` を返すことを確認してください。たとえば、`f(n) = (nothing, [0; children(n)])` は、すべてのノードが少なくとも1つの子を持つため、スタックオーバーフローを引き起こします。

効率的な反復を可能にする [`HasNodeType`](@ref) を持つ木を作成するには、代わりに [`StableNode`](@ref) を参照してください。

## 例

```julia
julia> t = [1, [2, 3]];

julia> f(n) = n isa AbstractArray ? (nothing, children(n)) : (n+1, children(n))

julia> treemap(f, t)
nothing
├─ 2
└─ nothing
   ├─ 3
   └─ 4

julia> g(n) = isempty(children(n)) ? (nodevalue(n), []) : (nodevalue(n), [0; children(n)])
g (generic function with 1 method)

julia> treemap(g, t)
Any[1, [2, 3]]
├─ 0
├─ 1
└─ [2, 3]
   ├─ 0
   ├─ 2
   └─ 3
```
