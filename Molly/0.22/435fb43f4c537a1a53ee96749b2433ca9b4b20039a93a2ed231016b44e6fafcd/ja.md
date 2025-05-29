```
log_property!(logger, system, neighbors=nothing, step_n=0;
              n_threads=Threads.nthreads(), kwargs...)
```

シミュレーション全体を通じてシステムのプロパティをログします。

カスタムロガーはこの関数を実装する必要があります。必要に応じて、ロガーに追加のキーワード引数を渡すことができます。
