# ConcurrentCollections

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/)

ConcurrentCollections.jlは、Julia ≥ 1.7のための以下の同時コレクションを提供します。ほとんどの操作は、適切な場合には（ほぼ）ロックフリーです。

  * [`DualLinkedConcurrentRingQueue`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.DualLinkedConcurrentRingQueue)
  * [`DualLinkedQueue`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.DualLinkedQueue)
  * [`LinkedConcurrentRingQueue`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.LinkedConcurrentRingQueue)
  * [`ConcurrentQueue`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.ConcurrentQueue)
  * [`ConcurrentStack`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.ConcurrentStack)
  * [`WorkStealingDeque`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.WorkStealingDeque)
  * [`ConcurrentDict`](https://juliaconcurrent.github.io/ConcurrentCollections.jl/dev/#ConcurrentCollections.ConcurrentDict)

**注意**: プログラムのパフォーマンス（特に*スループット*）を改善する方法を探している場合は、まず同時コレクションの使用を**避ける**方法を探すことを強くお勧めします。特に、同時プログラミングの困難を回避するために、[データ並列](https://juliafolds.github.io/data-parallelism/)パターンを適用することを検討してください。例えば、タスク間で共有される`ConcurrentDict`の代わりに、タスクローカルの**非**スレッドセーフな`Dict`を使用する方がしばしば良いアイデアです。データ並列プログラミングにおける最も重要な技術の1つは、そのようなタスクローカル状態をどのようにマージするかです。詳細については、例えば、[データ並列における変異に対する効率的かつ安全なアプローチ](https://juliafolds.github.io/data-parallelism/tutorials/mutations/)を参照してください。
