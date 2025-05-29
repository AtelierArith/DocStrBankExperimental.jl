```
set_scheduler!([scheduler]; kwargs...)
```

`OhMyThreads` マルチスレッドスケジューラのパラメータを設定します。

この関数は、`OhMyThreads.Scheduler` として `scheduler` を受け入れるか、対応するパラメータがキーワード引数として指定されるシンボルとして受け入れます。たとえば、チャンク処理が有効な4つのタスクを使用する静的スケジューラは、次のように設定できます。

```
set_scheduler!(StaticScheduler(; ntasks=4, chunking=true))
```

または、次のように同等に設定できます。

```
set_scheduler!(:static; ntasks=4, chunking=true)
```

すべてのスケジューラとそのキーワード引数の詳細な説明については、[OhMyThreads](https://juliafolds2.github.io/OhMyThreads.jl/stable/refs/api/#OhMyThreads.Schedulers.Scheduler) ドキュメントを参照してください。

`scheduler` が渡されず、キーワード引数のみが提供された場合、提供されたキーワード引数を使用して `DynamicScheduler` コンストラクタが使用されます。

スケジューラをデフォルト値にリセットするには、引数を渡さずに `set_scheduler!` を呼び出すと、デフォルトの `DynamicScheduler()` が使用されます。使用されるスレッドの数が1つだけの場合は、`SerialScheduler()` にフォールバックします。
