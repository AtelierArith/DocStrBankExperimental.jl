```
StableNode{T} <: AbstractNode{T}
```

すべてのノードが `StableNode{T}` 型である木に属するノード。この型は、[`NodeTypeUnknown`](@ref) を持つ木が、効率的なトラバーサルと反復を可能にするインデックス可能な `children` を持つ型安定な木に変換するためのメソッドを実装できるように提供されています。

## コンストラクタ

```julia
StableNode{T}(x::T, ch)
StableNode(x, ch=())
StableNode{T}(𝒻, node)
```

## 引数

  * `x`: [`nodevalue`](@ref) によって返される構築されたノードの値。
  * `ch`: ノードの子ノードで、各ノードは `StableNode` 型でなければなりません。
  * `𝒻`: 木のノードに対して呼び出されると、`StableNode` でラップされるべき値を返す関数。`𝒻` の戻り値は `T` に変換可能でなければなりません（例を参照）。
  * `T`: 木の `StableNode` の値の型。
  * `node`: `StableNode` 木を構築するために使用される木のノード。

## 例

```julia
t = [1, [2,3]]

node = StableNode{Union{Int,Nothing}}(t) do n
    n isa Integer ? convert(Int, n) : nothing
end
```

上記の例では、`node` は [`HasNodeType`](@ref) を持つ木で、`StableNode{Union{Int,Nothing}}` 型のノードを持っています。新しい木の配列に対応するノードは値が `nothing` であり、他のノードは対応する `Int` 値を持っています。
