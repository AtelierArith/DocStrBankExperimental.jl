```
tforeach(f, A::AbstractArray...;
         [scheduler::Union{Scheduler, Symbol} = :dynamic]) :: Nothing
```

`Base.foreach`のようなマルチスレッド関数。複数の並列タスクで`A`の各要素に`f`を適用し、`nothing`を返します。つまり、次のコードの並列版です。

```
for x in A
    f(x)
end
```

## 例:

```
using OhMyThreads: tforeach

tforeach(1:10) do i
    println(i^2)
end
```

## キーワード引数:

  * `scheduler::Union{Scheduler, Symbol}` (デフォルト `:dynamic`): 計算が並列タスクにどのように分割され、どのようにスケジュールされるかを決定します。利用可能なスケジューラに関する詳細は[`Scheduler`](@ref)を参照してください。

さらに、`tforeach`は**選択したスケジューラによってサポートされているすべてのキーワード引数**を受け入れます。それらは単に対応する`Scheduler`コンストラクタに渡されます。例:

```
tforeach(1:10; chunksize=2, scheduler=:static) do i
    println(i^2)
end
```

ただし、曖昧さを避けるために、これは現在**`scheduler::Symbol`に対してのみサポートされています**（`scheduler::Scheduler`にはサポートされていません）。
