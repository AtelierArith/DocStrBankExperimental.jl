```
tmap(f, [OutputElementType], A::AbstractArray...;
     [scheduler::Union{Scheduler, Symbol} = :dynamic])
```

`Base.map`のようなマルチスレッド関数。新しいコンテナを`A`に似た形で作成し、`i`番目の要素が`f(A[i])`に等しくなるように並行して埋めます。

オプション引数`OutputElementType`は、返されるコンテナの特定の要素タイプを選択し、一般的に`OutputElementType`が指定されていないバージョンよりも少ないアロケーションを発生させます。

## 例:

```
using OhMyThreads: tmap

tmap(sin, 1:10)
```

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}` (デフォルトは`:dynamic`): 計算が並行タスクにどのように分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。

さらに、`tmap`は**選択したスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。これらは単に対応する`Scheduler`コンストラクタに渡されます。例:

```
tmap(sin, 1:10; chunksize=2, scheduler=:static)
```

ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
