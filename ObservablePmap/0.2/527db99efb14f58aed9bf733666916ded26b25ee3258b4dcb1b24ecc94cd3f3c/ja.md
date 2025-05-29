```
summary, task = opmap(f, [::AbstractWorkerPool], c...;
                      schedule_now=true, summarize=default_summarize,
                      kwargs... )
```

コレクション `c` を変換するために、利用可能なワーカーとタスクを使用して各要素に `f` を適用します。これは `Distributed.pmap` を呼び出すことによって行われます。関数 `f` は最初の引数として呼び出し可能な `setmessage` を受け取り、ワーカーの現在のステータスを説明するステータスメッセージを設定するために `setmessage(msg)` を呼び出すことができます。返される `summary` は、すべてのワーカーのステータスとそのステータスメッセージを含む要約文字列を持つ `Observable` です。要約は、`summarize` キーワード引数を設定することでカスタマイズできます。

利用可能なワーカー全体で `f` の適用は、返された `task::Task` 内で非同期に行われます。`schedule_now=false` を設定すると、`opmap` がタスクをスケジュールするのを防ぎます。

`ObservablePmap` モジュールは、`opmap` を呼び出す前にすべてのワーカーでロードされている必要があります。例えば、`@everywhere using ObservablePmap` のようにします。

`opmap` に対する他の位置引数およびキーワード引数は、`pmap` と同じです。

例:

```jldoctest
@everywhere using ObservablePmap
using Observables # 以下の `map` メソッドのため
summ, task = opmap(1:5; on_error=identity) do setmessage, x
    for i=1:5
        setmessage("$i @ $x")
        (10i+x==33) && error("Error at $i")
        sleep(rand())
    end
end
html = map(x -> HTML("<pre>$x</pre>"), summ)
```
