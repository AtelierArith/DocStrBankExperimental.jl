```
treducemap(op, f, A::AbstractArray...;
           [scheduler::Union{Scheduler, Symbol} = :dynamic],
           [outputtype::Type = Any],
           [init])
```

`tmapreduce`と似ていますが、`f`と`op`の引数の順序が逆になっています。これは、`do`ブロック記法を使用する際に便利なことがあります。`A`に対して還元を行い、各要素に単一引数関数`f`を適用し、その後、二引数関数`op`でそれらを結合します。

`op`は**必ず**[結合的](https://en.wikipedia.org/wiki/Associative_property)な関数でなければなりません。つまり、`op(a, op(b, c)) ≈ op(op(a, b), c)`の意味でです。`op`が（おおよそ）結合的でない場合、未定義の結果が得られます。

## 例:

```
using OhMyThreads: treducemap

treducemap(+, √, [1, 2, 3, 4, 5])
```

は、次の形での`sum(√, [1, 2, 3, 4, 5])`の並列化されたバージョンです。

```
(√1 + √2) + (√3 + √4) + √5
```

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}`（デフォルト`:dynamic`）：計算がどのように並列タスクに分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。
  * `outputtype::Type`（デフォルト`Any`）：並列計算の出力型として主張される型として機能します。このオプションを設定する必要がないように[StableTasks.jl](https://github.com/JuliaFolds2/StableTasks.jl)を使用していますが、型の安定性に問題がある場合は、このキーワード引数を使用して回復できるかもしれません。
  * `init`：還元の初期値。計算のタスクローカルな逐次部分に対して`mapreduce`に転送されます。

さらに、`treducemap`は**選択されたスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。それらは単に対応する`Scheduler`コンストラクタに渡されます。例:

```
treducemap(+, √, [1, 2, 3, 4, 5]; chunksize=2, scheduler=:static)
```

ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
