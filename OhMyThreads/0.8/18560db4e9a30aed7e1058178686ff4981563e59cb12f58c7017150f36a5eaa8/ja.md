```
tmap!(f, out, A::AbstractArray...;
      [scheduler::Union{Scheduler, Symbol} = :dynamic])
```

`Base.map!`のようなマルチスレッド関数です。複数のタスクで並行して、この関数は`out[i] = f(A[i])`を`A`と`out`の各インデックス`i`に対して割り当てます。

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}` (デフォルトは`:dynamic`): 計算が並列タスクにどのように分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。

さらに、`tmap!`は**選択したスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。これらは単に対応する`Scheduler`コンストラクタに渡されます。ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
