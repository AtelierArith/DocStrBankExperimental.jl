```
LinkedConcurrentRingQueue{T}()
```

非ブロッキングの `push!` と [`maybepopfirst!`](@ref) を持つ同時実行キューです。

関連情報: [`DualLinkedConcurrentRingQueue`](@ref)

# 例

```jldoctest LinkedConcurrentRingQueue
julia> using ConcurrentCollections

julia> q = LinkedConcurrentRingQueue{Int}();

julia> push!(q, 111);

julia> push!(q, 222);

julia> maybepopfirst!(q)  # 先入れ先出し
Some(111)

julia> maybepopfirst!(q)
Some(222)

julia> maybepopfirst!(q) === nothing  # キューは空です
true
```

# 拡張ヘルプ

`LinkedConcurrentRingQueue` は、Morrison と Afek (2013) による Linked Concurrent Ring Queue (または Concurrent Ring Queues のリスト; LCRQ) に基づいています：

> Morrison, Adam, and Yehuda Afek. “Fast Concurrent Queues for X86 Processors.” In Proceedings of the 18th ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming, 103–112. PPoPP ’13. New York, NY, USA: Association for Computing Machinery, 2013. [https://doi.org/10.1145/2442516.2442527](https://doi.org/10.1145/2442516.2442527). (改訂版: [https://www.cs.tau.ac.il/~mad/publications/ppopp2013-x86queues.pdf](https://www.cs.tau.ac.il/~mad/publications/ppopp2013-x86queues.pdf))

