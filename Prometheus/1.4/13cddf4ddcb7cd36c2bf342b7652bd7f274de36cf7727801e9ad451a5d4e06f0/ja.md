```
Prometheus.ProcessCollector(pid; registry=DEFAULT_REGISTRY)
```

指定された `pid` 関数によって与えられたプロセス ID のためのプロセスコレクタを作成します。このコレクタは、プロセスの CPU 時間、開始時間、メモリ使用量、ファイル使用量、および I/O 操作に関するメトリクスを公開します。

**引数**

  * `pid :: Function`: メトリクスを収集するためのプロセス ID を文字列または整数として返す関数。デフォルトでは `"self"` pid が使用され、つまり現在のプロセスが使用されます。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。デフォルトではデフォルトのレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。

!!! note
    現在のプロセスのための `ProcessCollector` は、デフォルトのレジストリに自動的に登録されます。必要に応じて、次のように呼び出すことで削除できます。

    ```julia
    Prometheus.unregister(Prometheus.DEFAULT_REGISTRY, Prometheus.PROCESS_COLLECTOR)
    ```


!!! note
    プロセスコレクタは現在、Linux のみで利用可能です。これは `/proc` ファイルシステムを必要とするためです。Windows および macOS では、このコレクタはメトリクスを公開しません。

