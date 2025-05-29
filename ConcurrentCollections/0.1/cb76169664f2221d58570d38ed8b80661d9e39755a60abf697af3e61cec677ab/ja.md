```
WorkStealingDeque{T}()
```

型 `T` のオブジェクトのための並行ワークスティーリング「デック」。

これは完全なデックではなく、以下の点において制限があります：

  * コレクションの末尾で動作する `push!` と [`maybepop!`](@ref) は、単一のタスクによってのみ実行できます。
  * ヘッドで要素を取得して削除するための [`maybepopfirst!`](@ref)（別名：スティール）は、任意のタスクから呼び出すことができます。ただし、`pushfirst!` はありません。

# 例

```jldoctest WorkStealingDeque
julia> using ConcurrentCollections

julia> deque = WorkStealingDeque{Int}();

julia> push!(deque, 1);

julia> push!(deque, 2);

julia> push!(deque, 3);

julia> maybepop!(deque)
Some(3)

julia> fetch(Threads.@spawn maybepopfirst!(deque))
Some(1)

julia> fetch(Threads.@spawn popfirst!(deque))
2

julia> maybepopfirst!(deque)  # 何も返さない
```

# 拡張ヘルプ

現在の実装は、C/C++ メモリモデル（Julia のメモリモデルが設計されているモデル）に完全には準拠していないことが知られています。

これは、Chase と Lev (2005) による動的円形ワークスティーリングデックを実装しています：

> Chase, David, and Yossi Lev. “Dynamic Circular Work-Stealing Deque.” In Proceedings of the Seventeenth Annual ACM Symposium on Parallelism in Algorithms and Architectures, 21–28. SPAA ’05. New York, NY, USA: Association for Computing Machinery, 2005. [https://doi.org/10.1145/1073970.1073974](https://doi.org/10.1145/1073970.1073974).

