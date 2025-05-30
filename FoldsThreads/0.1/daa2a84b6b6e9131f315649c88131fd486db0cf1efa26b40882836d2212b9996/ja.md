# FoldsThreads: JuliaFolds2/*.jl用の追加スレッド実行者

[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliafolds.github.io/FoldsThreads.jl/dev) [![GitHub Actions](https://github.com/JuliaFolds/FoldsThreads.jl/workflows/Run%20tests/badge.svg)](https://github.com/JuliaFolds/FoldsThreads.jl/actions?query=workflow%3ARun+tests)

FoldsThreads.jlは、[Transducers.jl](https://github.com/JuliaFolds/Transducers.jl)や[FLoops.jl](https://github.com/JuliaFolds/FLoops.jl)などのさまざまなJuliaFolds/*.jlパッケージで使用できる追加のスレッドベースの実行者を提供します。

```
                                  Executors
                           ,----------------------.
     Algorithms            |    FoldsThreads.jl    |         Data structures
,------------------.       |-----------------------|       ,-----------------.
|  FLoops,         |       |  ThreadedEx*          |       |  Array,         |
|  Folds,          |       |  WorkStealingEx,      |       |  Tables,        |
|  Transducers,    |  ---  |  DepthFirstEx,        |  ---  |  FGenerators,   |
|  OnlineStats,    |       |  TaskPoolEx,          |       |  Dict,          |
|  DataTools, ...  '       |  NondeterministicEx,  |       |  Set, ...       |
`------------------'       |  ...                  |       `-----------------'
                           `-----------------------'
```

(* `ThreadedEx`はTransducers.jlによって提供されるデフォルトの実行者です)

  * `WorkStealingEx`は作業の盗用（継続の盗用）を実装します。負荷分散に役立ちます。
  * `DepthFirstEx`は深さ優先スケジューリングを実装します。`findfirst`型の計算に役立ちます。
  * `TaskPoolEx`: タスクプール実行者。細かい実行制御（例：バックプレッシャーや「バックグラウンド」スレッド）に役立ちます。
  * `NondeterministicEx`: 非並列化可能なイテレータを使用して計算を並列化するための実行者です。
