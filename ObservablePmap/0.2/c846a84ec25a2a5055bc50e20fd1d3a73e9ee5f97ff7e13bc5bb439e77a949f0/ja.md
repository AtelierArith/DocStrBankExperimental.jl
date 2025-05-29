```
summary, task = ologpmap(f, [::AbstractWorkerPool], c...;
                      logger_f=SimpleLogger, schedule_now=true,
                      summarize=default_summarize,
                      kwargs... )
```

コレクション `c` を変換するために、利用可能なワーカーとタスクを使用して各要素に `f` を適用し、`Distributed.pmap` を呼び出します。返される `summary` は、各ワーカーの最後のログメッセージの要約文字列を含む `Observable` です（各ワーカーが `Logging` インターフェースを使用して発信します）。キーワード引数 `logger_f` は、各ワーカー内部の `IOBuffer` で呼び出され、このバッファにメッセージを書き込むロガーを作成します。このバッファから読み取られたログメッセージは、observable `summary` に含まれるワーカーの現在のステータスメッセージとして使用されます。

要約は、`summarize` キーワード引数を設定することでカスタマイズできます。

`ObservablePmap` モジュールは、`ologpmap` を呼び出す前にすべてのワーカーでロードされている必要があります。例えば、`@everywhere using ObservablePmap` のようにします。

`ologpmap` に対する他の位置引数およびキーワード引数は、`opmap` と同じです。

例:

```jldoctest
@everywhere using ObservablePmap
@everywhere using ProgressLogging
@everywhere using TerminalLoggers
summ, task = ologpmap( 'a':'e', 2:2:10;
                       on_error=identity, logger_f=TerminalLogger ) do c, x
    @withprogress name="processing '$c'" for i=1:x
        sleep(rand())
        @logprogress i/x
    end
    @info "finished '$c'"
    x
end
html = map(x -> HTML("<pre>$x</pre>"), summ)
```
