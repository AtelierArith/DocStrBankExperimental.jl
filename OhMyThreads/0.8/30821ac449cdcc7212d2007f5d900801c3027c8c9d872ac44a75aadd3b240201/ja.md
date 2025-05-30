```
treduce(op, A::AbstractArray...;
        [scheduler::Union{Scheduler, Symbol} = :dynamic],
        [outputtype::Type = Any],
        [init])
```

`Base.reduce`のようなマルチスレッド関数です。二引数関数`op`を使用して`A`に対して還元を行います。

`op`は**必ず**[結合的](https://en.wikipedia.org/wiki/Associative_property)な関数でなければなりません。つまり、`op(a, op(b, c)) ≈ op(op(a, b), c)`の形を満たす必要があります。`op`が（おおよそ）結合的でない場合、未定義の結果が得られます。

## 例:

```
using OhMyThreads: treduce

treduce(+, [1, 2, 3, 4, 5])
```

は、次の形で`sum([1, 2, 3, 4, 5])`の並列化されたバージョンです。

```
(1 + 2) + (3 + 4) + 5
```

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}`（デフォルトは`:dynamic`）：計算がどのように並列タスクに分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。
  * `outputtype::Type`（デフォルトは`Any`）：並列計算の出力型として主張される型として機能します。このオプションを設定する必要がないように[StableTasks.jl](https://github.com/JuliaFolds2/StableTasks.jl)を使用していますが、型の安定性に問題がある場合は、このキーワード引数を使用して回復できるかもしれません。
  * `init`：還元の初期値。計算のタスクローカルな逐次部分に対して`mapreduce`に渡されます。

さらに、`treduce`は**選択したスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。それらは単に対応する`Scheduler`コンストラクタに渡されます。例:

```
treduce(+, [1, 2, 3, 4, 5]; chunksize=2, scheduler=:static)
```

ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
