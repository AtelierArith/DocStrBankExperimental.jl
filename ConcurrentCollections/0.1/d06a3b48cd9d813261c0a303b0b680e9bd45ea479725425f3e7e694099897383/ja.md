```
DualLinkedConcurrentRingQueue{T}()
```

「ほぼ」ノンブロッキングの `push!` と `popfirst!` を持つ同時キューです。空のキューで `popfirst!` を呼び出すと、別のタスクでの `push!` を待機します。

関連情報: [`LinkedConcurrentRingQueue`](@ref), [`DualLinkedQueue`](@ref)

# 例

```jldoctest DualLinkedConcurrentRingQueue
julia> using ConcurrentCollections

julia> q = DualLinkedConcurrentRingQueue{Int}();

julia> push!(q, 111);

julia> push!(q, 222);

julia> popfirst!(q)  # 先入れ先出し
111

julia> popfirst!(q)
222
```

# 拡張ヘルプ

`popfirst!` は空のキューで呼び出すとブロックするため、`DualLinkedConcurrentRingQueue` はほぼ無制限の `Base.Channel` のように動作します。ただし、`DualLinkedConcurrentRingQueue` は制限を超えた場合の `push!` での `close` やブロッキングをサポートしていません。

`DualLinkedConcurrentRingQueue` は他の同時キュー実装と比較して非常に優れた性能を発揮します。ただし、リンクされた固定サイズのバッファに基づいているため、比較的大きなメモリオーバーヘッドがあります。

`DualLinkedConcurrentRingQueue` は、Izraelevitz と Scott (2017) によるリンクされた多極性二重リングキューに基づいています：

> Izraelevitz, Joseph, and Michael L. Scott. “Generality and Speed in Nonblocking Dual Containers.” ACM Transactions on Parallel Computing 3, no. 4 (March 23, 2017): 22:1–22:37. [https://doi.org/10.1145/3040220](https://doi.org/10.1145/3040220).

