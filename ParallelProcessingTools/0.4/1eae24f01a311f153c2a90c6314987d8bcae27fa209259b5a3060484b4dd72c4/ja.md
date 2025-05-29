```
FlexWorkerPool{WP<:AbstractWorkerPool}(
    worker_pids::AbstractVector{Int};
    label::AbstractString = "", maxoccupancy::Int = 1, init_workers::Bool = true
)::AbstractWorkerPool

FlexWorkerPool(; caching = false, withmyid::Bool = true, kwargs...)
```

動的にJuliaプロセスを追加および削除できるクラスターマネージャーと連携することを目的とした柔軟なワーカープールです。

現在のプロセス（`Distributed.myid()`）がプールの一部である場合、または`withmyid`が`true`である場合、他のワーカーがプールのメンバーでないときのフォールバックとして使用されます（例えば、他のプロセスがまだ追加されていない場合や、プール内の他のすべてのプロセスが終了して削除された場合）。現在のプロセスは、他のすべてのワーカーが現在使用中の場合にはフォールバックとして使用されません。

`caching`がtrueの場合、プールは基盤となるプールとして`Distributed.CachingPool`を使用します。それ以外の場合は`Distributed.WorkerPool`を使用します。

`maxoccupancy`が1より大きい場合、個々のワーカーは`maxoccupancy`回並行して使用できます。したがって、`take!(pool)`は、間に`put!(pool, pid)`がなくても同じプロセスID `pid`を複数回返すことがあります。このような（理想的には適度な）オーバーサブスクリプションは、ワーカーのレイテンシー関連のアイドル時間を減らすのに役立ちます。例えば、ワーカーへの通信レイテンシーが呼び出される関数の実行時間に比べて短くない場合や、リモート関数がI/Oを待ってブロックされることが多い場合です。注意: ワーカーは、プールから取得された回数と同じ回数だけ戻される必要があります。

`init_workers`が`true`の場合、プールから取得されたワーカーは、現在のグローバル初期化レベルに初期化されることが保証されます（[`@always_everywhere`](@ref)を参照）。

`WP`は使用される基盤となるワーカープールの型で、例えば`Distributed.WorkerPool`（デフォルト）または`Distributed.CachingPool`です。

例:

```julia
using ParallelProcessingTools, Distributed

pool = FlexWorkerPool(withmyid = true, maxoccupancy = 3)

workers(pool)

pids = [take!(pool) for _ in 1:3]
@assert pids == repeat([myid()], 3)
foreach(pid -> put!(pool, pid), pids)

addprocs(4)
worker_procs = workers()
push!.(Ref(pool), worker_procs)

pids = [take!(pool) for _ in 1:4*3]
@assert pids == repeat(worker_procs, 3)
foreach(pid -> put!(pool, pid), pids)
rmprocs(worker_procs)

pids = [take!(pool) for _ in 1:3]
@assert pids == repeat([myid()], 3)
foreach(pid -> put!(pool, pid), pids)
```
