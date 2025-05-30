```
tcollect([OutputElementType], gen::Union{AbstractArray, Generator{<:AbstractArray}};
         [scheduler::Union{Scheduler, Symbol} = :dynamic])
```

`Base.collect`のようなマルチスレッド関数です。基本的には、生成関数と入力に対して`tmap`を呼び出すだけです。

オプション引数`OutputElementType`は、返されるコンテナの特定の要素タイプを選択し、一般的に`OutputElementType`が指定されていないバージョンよりも少ないアロケーションが発生します。

## 例:

```
using OhMyThreads: tcollect

tcollect(sin(i) for i in 1:10)
```

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}` (デフォルトは`:dynamic`): 計算がどのように並列タスクに分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。

さらに、`tcollect`は**選択したスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。それらは単に対応する`Scheduler`コンストラクタに渡されます。例:

```
tcollect(sin(i) for i in 1:10; chunksize=2, scheduler=:static)
```

ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
